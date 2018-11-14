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
ms.openlocfilehash: 8a20e337cddcc45701f20941ac5d7fea5e4324a5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330304"
---
# <a name="thread-local-storage"></a>Úložiště Thread Local

**Specifické pro Microsoft**

Místní úložiště vláken (TLS) je mechanismus, podle kterého všechna vlákna daného procesu alokují prostor pro data určitého vlákna. U standardních aplikací s více vlákny jsou data sdílena mezi všemi vlákny daného procesu, kde místní úložiště vláken představuje mechanismus pro rozdělení dat pro vlákno. Úplný popis vláken naleznete v tématu [procesy a vlákna](/windows/desktop/ProcThread/processes-and-threads) v sadě Windows SDK.

Jazyk Microsoft C obsahuje atribut Rozšířené paměťové třídy, vlákna, která se používá s __declspec – klíčové slovo pro deklarování místní proměnné vlákna. Například následující kód deklaruje místní proměnnou vlákna integer a inicializuje ji hodnotou:

```
__declspec( thread ) int tls_i = 1;
```

Když deklarujete staticky vázané vlákno lokálních proměnných, musí být dodržovány tyto pokyny:

- Místní proměnné vlákna, které mají dynamická inicializace jsou inicializovány pouze na vlákně, které způsobí, že knihovna DLL pro načtení a vlákna, na kterých už běží v procesu. Další informace najdete v tématu [vlákno](../cpp/thread.md).

- Atribut thread můžou použít jenom u dat deklarace a definice. Nelze použít v deklaracích nebo definicích funkce. Například následující kód vygeneruje chybu kompilátoru:

    ```C
    #define Thread   __declspec( thread )
    Thread void func();      /* Error */
    ```

- Atribut thread můžete zadat pouze na položky dat s trváním statického úložiště. To zahrnuje globální data (static a extern) a místní statická data. Nelze deklarovat automatické data s atributem vlákna. Například následující kód vygeneruje chyby kompilátoru:

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

- Atribut thread je nutné použít pro deklarace a definice dat thread local, bez ohledu na to, zda deklarace a definice objeví ve stejném souboru nebo v samostatných souborech. Například následující kód vygeneruje chybu:

    ```C
    #define Thread   __declspec( thread )
    extern int tls_i;     /* This generates an error, because the   */
    int Thread tls_i;     /* declaration and the definition differ. */
    ```

- Atribut vlákna nelze použít jako modifikátor typu. Například následující kód vygeneruje chybu kompilátoru:

    ```C
    char *ch __declspec( thread );      /* Error */
    ```

- Adresu místní proměnné vlákna není považována za konstantu a libovolný výraz zahrnující takové adresy se nepovažuje za konstantní výraz. To znamená, že nelze použít adresu místní proměnné vlákna jako inicializátor pro ukazatel. Například kompilátor označí jako chyba následující kód:

    ```C
    #define Thread   __declspec( thread )
    Thread int tls_i;
    int *p = &tls_i;      /* Error */
    ```

- C umožňuje inicializaci proměnné s výrazem zahrnujícím odkaz sám na sebe, ale pouze pro nestatické objekty. Příklad:

    ```C
    #define Thread   __declspec( thread )
    Thread int tls_i = tls_i;             /* Error */
    int j = j;                            /* Error */
    Thread int tls_i = sizeof( tls_i )    /* Okay  */
    ```

   Mějte na paměti, že operátor sizeof: výraz, který obsahuje proměnné, který je inicializován nepředstavuje odkaz sám na sebe a je povolen.

- Použití  **\_ \_declspec(thread)** může kolidovat s [zpoždění načítání](../build/reference/linker-support-for-delay-loaded-dlls.md) importů knihoven DLL.

Další informace o používání atribut vlákna, naleznete v tématu [Témata multithreadingu](../parallel/multithreading-support-for-older-code-visual-cpp.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)