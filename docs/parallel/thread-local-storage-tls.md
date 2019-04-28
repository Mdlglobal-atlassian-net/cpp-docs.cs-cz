---
title: Lokální úložiště vláken (TLS)
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
ms.openlocfilehash: f5a75f7964b0291a980b22d36e7ce6a0a87d3dc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362722"
---
# <a name="thread-local-storage-tls"></a>Lokální úložiště vláken (TLS)

Místní úložiště vláken (TLS) je metoda, podle kterého všechna vlákna daného procesu můžete přidělit umístění, ve kterých se mají ukládat data určitého vlákna. Dynamicky datové vazby (za běhu) specifické pro vlákno je podporováno prostřednictvím rozhraní API pro protokol TLS ([TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc).  Win32 a kompilátor Visual C++ teď podporují staticky vazbou (během načítání) dat pro vlákno kromě stávající implementaci rozhraní API.

##  <a name="_core_compiler_implementation_for_tls"></a> Implementace kompilátoru TLS

**C++11:**  `thread_local` Specifikátor třídy úložiště je doporučeným způsobem, jak určit úložiště thread-local se pro objekty a členy třídy. Další informace najdete v tématu [třídy úložiště (C++)](../cpp/storage-classes-cpp.md).

Atribut specifické pro společnost Microsoft poskytuje jazyk Visual C++ [vlákno](../cpp/thread.md), jako modifikátor třídy rozšířené úložiště. Použití **__declspec** – klíčové slovo k deklaraci **vlákno** proměnné. Například následující kód deklaruje místní proměnnou vlákna integer a inicializuje ji hodnotou:

```
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>Pravidla a omezení

Při deklarování staticky vázaného místními objekty vlákna a proměnné, musí být dodrženy následující pokyny. Tyto pokyny platí i pro [vlákno](../cpp/thread.md)a ve většině případů také do [thread_local](../cpp/storage-classes-cpp.md):

- **Vlákno** atribut lze použít pouze pro třídy a data deklarací a definic. Nelze použít v deklaracích nebo definicích funkce. Například následující kód vygeneruje chybu kompilátoru:

    ```
    __declspec( thread )void func();     // This will generate an error.
    ```

- **Vlákno** modifikátor může být určen pouze na položky dat se **statické** rozsahu. To zahrnuje globální datové objekty (obojí **statické** a **extern**), místní statické objekty a statické datové členy třídy jazyka C++. Automatické datové objekty nelze deklarovat s **vlákno** atribut. Následující kód vygeneruje chyby kompilátoru:

    ```
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )    // This will generate an error.
    {
        return tls_i;
    }
    ```

- Deklarace a definice místního objektu musí být specifikovány vlákno **vlákno** atribut. Například následující kód vygeneruje chybu:

    ```
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- **Vlákno** atributu nelze použít jako modifikátor typu. Například následující kód vygeneruje chybu kompilátoru:

    ```
    char __declspec( thread ) *ch;        // Error
    ```

- Vzhledem k tomu, že deklarace jazyka C++ objekty, které používají **vlákno** atribut je povolen, následující dva příklady jsou sémanticky ekvivalentní:

    ```
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

- Adresa místního objektu vlákna není považována za konstantu a libovolný výraz zahrnující takové adresy se nepovažuje za konstantní výraz. Ve standardním C je důsledkem tohoto zakázat použití adresu místní proměnné vlákna jako inicializátor objektu nebo ukazatele. Například následující kód je označen jako chyba v kompilátoru jazyka C:

    ```
    __declspec( thread )int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

   Toto omezení neplatí v jazyce C++. Protože jazyk C++ umožňuje pro dynamická inicializace všech objektů, je objekt inicializovat pomocí výrazu, který používá adresu místní proměnné vlákna. To lze provést stejně jako konstrukce místními objekty vlákna. Příklad kódu uvedeného výše nevygeneruje chybu při kompilaci jako zdrojový soubor jazyka C++. Všimněte si, že adresu místní proměnné vlákna je platný pouze dokud vlákno, ve kterém byla získána adresu stále existuje.

- Standard jazyka C umožňuje inicializaci objektu nebo proměnné s výrazem zahrnujícím odkaz sám na sebe, ale pouze pro nestatické objekty. Přestože jazyk C++ obvykle umožňuje takovou dynamickou inicializaci objektu s výrazem zahrnujícím odkaz sám na sebe, tento typ inicializace není povolen s místními objekty vlákna. Příklad:

    ```
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

   Všimněte si, že `sizeof` výraz, který obsahuje inicializovaný objekt, nepředstavuje odkaz sám na sebe a je povolen v jazyce C a C++.

   Jazyk C++ neumožňuje takovou dynamickou inicializaci vlákna dat z důvodu možných budoucí vylepšení zařízení místní úložiště vláken.

- V operačních systémech Windows než Windows Vista `__declspec`(vlákno) má určitá omezení. Pokud knihovna DLL deklaruje data ani jako objekt `__declspec`(vlákno), může to způsobit selhání ochrany Pokud dynamicky načíst. Po načtení knihovny DLL s [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya), dojde k selhání systému pokaždé, když se kód odkazuje `__declspec`data (vlákno). Vzhledem k tomu, že v době běhu je přiděleno globální proměnné místo pro vlákno, velikost toto místo je založená na výpočtu požadavkům aplikace a všechny knihovny DLL staticky propojené požadavky. Při použití `LoadLibrary`, nelze rozšířit tento prostor pro místní proměnné vlákna deklarované pomocí `__declspec`(vlákno). Použít rozhraní API pro protokol TLS, například [TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc), v knihovně DLL přidělit TLS, pokud knihovna DLL může být načten s `LoadLibrary`.

## <a name="see-also"></a>Viz také:

[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)
