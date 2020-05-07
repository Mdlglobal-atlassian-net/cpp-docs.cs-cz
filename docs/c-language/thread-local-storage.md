---
title: Úložiště Thread Local
ms.date: 11/04/2016
helpviewer_keywords:
- thread-local variables
- TLS (thread local storage)
- thread storage-class attribute
- thread-local storage
- storage, thread local storage
ms.assetid: a0f1b109-c953-4079-aa10-e47f5483173d
ms.openlocfilehash: a1099228e072a772ee7d8e7e93253b674d0cd24b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500269"
---
# <a name="thread-local-storage"></a>Úložiště Thread Local

**Specifické pro Microsoft**

Místní úložiště vláken (TLS) je mechanismus, kterým každé vlákno v daném vícevláknovém procesu přiděluje úložiště pro data specifická pro vlákno. U standardních aplikací s více vlákny jsou data sdílena mezi všemi vlákny daného procesu, kde místní úložiště vláken představuje mechanismus pro rozdělení dat pro vlákno. Úplnou diskuzi o vláknech naleznete v tématu [procesy a vlákna](/windows/win32/ProcThread/processes-and-threads) v Windows SDK.

Jazyk Microsoft C zahrnuje rozšířený atribut třídy úložiště, který se používá s klíčovým slovem __declspec k deklarování thread local proměnné. Například následující kód deklaruje celočíselnou thread local proměnnou a inicializuje ji hodnotou:

```
__declspec( thread ) int tls_i = 1;
```

Při deklaraci staticky vázaných thread local proměnných je nutné dodržovat tyto pokyny:

- Proměnné místního vlákna, které mají dynamickou inicializaci, jsou inicializovány pouze ve vlákně, které způsobí načtení knihovny DLL, a vláken, která jsou již spuštěna v procesu. Další informace naleznete v tématu [thread](../cpp/thread.md).

- Atribut thread lze použít pouze pro deklarace a definice dat. Nedá se použít pro deklarace a definice funkcí. Například následující kód vygeneruje chybu kompilátoru:

    ```C
    #define Thread   __declspec( thread )
    Thread void func();      /* Error */
    ```

- Atribut vlákna lze zadat pouze pro datové položky s trváním statického úložiště. To zahrnuje globální data (staticky i extern) a místní statická data. Nelze deklarovat Automatická data s atributem vlákna. Například následující kód generuje chyby kompilátoru:

    ```C
    #define Thread   __declspec( thread )
    void func1()
    {
        Thread int tls_i;            /* Error */
    }

    int func2( Thread int tls_i )    /* Error */
    {
       return tls_i;
    }
    ```

- Je nutné použít atribut thread pro deklaraci a definici thread localch dat, bez ohledu na to, zda se deklarace a definice vyskytují ve stejném souboru nebo samostatných souborech. Například následující kód vygeneruje chybu:

    ```C
    #define Thread   __declspec( thread )
    extern int tls_i;     /* This generates an error, because the   */
    int Thread tls_i;     /* declaration and the definition differ. */
    ```

- Atribut thread nelze použít jako modifikátor typu. Například následující kód vygeneruje chybu kompilátoru:

    ```C
    char *ch __declspec( thread );      /* Error */
    ```

- Adresa thread local proměnné není považována za konstantu a jakýkoliv výraz, který tuto adresu zahrnuje, není považován za konstantní výraz. To znamená, že nelze použít adresu thread local proměnné jako inicializátor pro ukazatel. Například kompilátor označí následující kód jako chybu:

    ```C
    #define Thread   __declspec( thread )
    Thread int tls_i;
    int *p = &tls_i;      /* Error */
    ```

- Jazyk C umožňuje inicializaci proměnné s výrazem, který zahrnuje odkaz sám na sebe, ale pouze pro objekty nestatického rozsahu. Příklad:

    ```C
    #define Thread   __declspec( thread )
    Thread int tls_i = tls_i;             /* Error */
    int j = j;                            /* Error */
    Thread int tls_i = sizeof( tls_i )    /* Okay  */
    ```

   Všimněte si, že výraz sizeof obsahující proměnnou, která je inicializována, nepředstavuje odkaz sám na sebe a je povolen.

- ** \_Použití \_declspec (thread)** může kolidovat s [opožděným načítáním](../build/reference/linker-support-for-delay-loaded-dlls.md) importů knihoven DLL.

Další informace o použití atributu thread naleznete v tématu [Multithreading – témata](../parallel/multithreading-support-for-older-code-visual-cpp.md).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)
