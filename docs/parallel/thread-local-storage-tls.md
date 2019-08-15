---
title: Lokální úložiště vláken (TLS)
ms.date: 08/09/2019
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
ms.openlocfilehash: 7e308f7ba23503879f8ebbcacde481cf72055229
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510388"
---
# <a name="thread-local-storage-tls"></a>Lokální úložiště vláken (TLS)

Místní úložiště vláken (TLS) je metoda, pomocí které každé vlákno v daném vícevláknovém procesu může přidělit umístění, do kterých mají být ukládána data specifická pro vlákno. Dynamicky vázaná data pro vlákna závislá na vláknech jsou podporována způsobem rozhraní TLS API ([TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc). Win32 a kompilátor Microsoftu C++ teď podporují společně s existující implementací rozhraní API staticky vázaná data (zatížení) na vlákno.

## <a name="_core_compiler_implementation_for_tls"></a>Implementace kompilátoru pro TLS

**C++ 11:**  Specifikátor `thread_local` třídy úložiště je doporučeným způsobem, jak zadat místní úložiště vlákna pro objekty a členy třídy. Další informace naleznete v tématu [třídy úložiště (C++)](../cpp/storage-classes-cpp.md).

MSVC také poskytuje atribut specifický pro společnost Microsoft, [vlákno](../cpp/thread.md)jako rozšířený modifikátor třídy úložiště. K deklaraci proměnné **vlákna** použijte klíčové slovo **__declspec** . Například následující kód deklaruje celočíselnou thread local proměnnou a inicializuje ji hodnotou:

```C
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>Pravidla a omezení

Při deklarování staticky vázaných thread local objektů a proměnných musí být pozorovány následující pokyny. Tyto pokyny platí jak pro [vlákno](../cpp/thread.md) , tak pro [thread_local](../cpp/storage-classes-cpp.md):

- Atribut **thread** lze použít pouze pro deklarace tříd a dat a definice. Nedá se použít pro deklarace a definice funkcí. Například následující kód vygeneruje chybu kompilátoru:

    ```C
    __declspec( thread )void func();     // This will generate an error.
    ```

- Modifikátor **vlákna** lze zadat pouze pro položky dat se statickým rozsahem. Který zahrnuje globální datové objekty ( **static** i **extern**), místní statické objekty a statické datové členy C++ tříd. Automatické datové objekty nelze deklarovat s atributem **thread** . Následující kód vygeneruje chyby kompilátoru:

    ```C
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )     // This will generate an error.
    {
        return tls_i;
    }
    ```

- Deklarace a definice objektu thread local musí všechny určovat atribut **vlákna** . Například následující kód vygeneruje chybu:

    ```C
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- Atribut **thread** nelze použít jako modifikátor typu. Například následující kód vygeneruje chybu kompilátoru:

    ```C
    char __declspec( thread ) *ch;        // Error
    ```

- Vzhledem k tomu, C++ že je povolena deklarace objektů, které používají atribut **thread** , jsou následující dva příklady sémanticky ekvivalentní:

    ```cpp
    __declspec( thread ) class B
    {
    // Code
    } BObject;  // OK--BObject is declared thread local.

    class B
    {
    // Code
    };
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.
    ```

- Adresa thread localho objektu není považována za konstantu a jakýkoliv výraz, který tuto adresu zahrnuje, není považován za konstantní výraz. V jazyce Standard C je efekt zakázat použití adresy thread local proměnné jako inicializátoru objektu nebo ukazatele. Například následující kód je označen jako chyba kompilátoru jazyka C:

    ```C
    __declspec( thread ) int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

   Toto omezení se nevztahuje na C++. Vzhledem C++ k tomu, že umožňuje dynamickou inicializaci všech objektů, lze inicializovat objekt pomocí výrazu, který používá adresu Thread Local proměnné. To se provádí stejně jako konstrukce thread local objektů. Například kód uvedený výše negeneruje chybu, když je kompilován jako C++ zdrojový soubor. Adresa thread local proměnné je platná pouze tak dlouho, dokud vlákno, ve kterém se adresa převzala, stále existuje.

- Standard jazyka C umožňuje inicializaci objektu nebo proměnné s výrazem, který zahrnuje odkaz sám na sebe, ale pouze pro objekty nestatického rozsahu. I C++ když obecně umožňuje takovou dynamickou inicializaci objektů s výrazem, který zahrnuje odkaz sám na sebe, tento druh inicializace není u Thread localch objektů povolen. Příklad:

    ```C
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

   Výraz, který obsahuje inicializovaný objekt, nepředstavuje odkaz sám na sebe a je povolen v C i C++ `sizeof`

   C++neumožňuje takovou dynamickou inicializaci dat vlákna z důvodu možného budoucího vylepšení thread local úložného zařízení.

- V operačních systémech Windows před systémem Windows Vista `__declspec( thread )` má některá omezení. Pokud knihovna DLL deklaruje jakákoli data nebo objekt jako `__declspec( thread )`, může dojít k chybě ochrany, pokud je dynamicky načten. Po načtení knihovny DLL pomocí funkce [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)dojde k selhání systému vždy, když kód odkazuje `__declspec( thread )` na data. Vzhledem k tomu, že globální proměnná prostor pro vlákno je přidělena v době běhu, je velikost tohoto místa založena na výpočtu požadavků aplikace a požadavků všech knihoven DLL, které jsou staticky propojeny. Když použijete `LoadLibrary`, nemůžete tento prostor zvětšit, aby bylo možné použít proměnné Thread Local `__declspec( thread )`deklarované s. Pomocí rozhraní API TLS, jako je například [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc), můžete v knihovně DLL přidělit protokol TLS, pokud může být knihovna `LoadLibrary`DLL načtena s.

## <a name="see-also"></a>Viz také:

[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)
