---
title: vlákno
ms.date: 05/07/2019
f1_keywords:
- thread_cpp
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
ms.openlocfilehash: 59a1af8a7eb73207f84ddf2194d5fe9e77d7d46a
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221958"
---
# <a name="thread"></a>vlákno

**Microsoft Specific**

**Vlákno** modifikátor rozšířené paměťové třídy se používá k deklarování místní proměnné vlákna. Přenosná ekvivalentní v C ++ 11 a novějším, použijte [thread_local](../cpp/storage-classes-cpp.md#thread_local) specifikátor třídy úložiště pro přenosného kódu. Na Windows `thread_local` je implementováno s **__declspec(thread)**.

## <a name="syntax"></a>Syntaxe

> **__declspec (vlákno)** *deklarátorů*

## <a name="remarks"></a>Poznámky

Místní úložiště vláken (TLS) je mechanismus, podle kterého všechna vlákna procesu alokují prostor pro data určitého vlákna. U standardních aplikací s více vlákny jsou data sdílena mezi všemi vlákny daného procesu, kde místní úložiště vláken představuje mechanismus pro rozdělení dat pro vlákno. Úplný popis vláken naleznete v tématu [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Deklarace místních proměnných vlákna musí použít [rozšířené syntaxe atributů](../cpp/declspec.md) a **__declspec** – klíčové slovo se **vlákno** – klíčové slovo. Například následující kód deklaruje místní proměnnou vlákna integer a inicializuje ji hodnotou:

```cpp
__declspec( thread ) int tls_i = 1;
```

Při použití místní proměnné vlákna v dynamicky načíst knihovny, musíte mít na paměti faktory, které může způsobit, že proměnná místního vlákna nebyla správně inicializována:

1. Pokud proměnná je inicializována pomocí volání funkce (včetně konstruktory), tato funkce bude volat pouze vlákna, která způsobila binární/knihovny DLL pro načtení do procesu a tato vlákna, které se spustí po načtení binárního souboru knihovny DLL. Inicializační funkce nejsou volány pro ostatní vlákna, který byl již spuštěn při načtení knihovny DLL. Dynamická inicializace probíhá na volání funkce DllMain pro DLL_THREAD_ATTACH, ale knihovny DLL nikdy získá, které zprávy, není-li knihovny DLL v procesu při spuštění vlákna.

1. Místní proměnné vlákna, které jsou staticky inicializována s konstantní hodnoty jsou obecně správně inicializována na všech vláknech. Však k prosinci 2017 existuje problém známé shoda v Microsoftu C++ kompilátoru kterým přijímat dynamické místo Statická inicializace proměnné constexpr.

   Poznámka: Oba zmíněné problémy se očekává v budoucnu vyřešit aktualizací kompilátoru.

Kromě toho musí dodržovat tyto pokyny při deklarování proměnné a místními objekty vlákna:

- Můžete použít **vlákno** atribut pouze pro třídy a deklarace a definice dat; **vlákno** nelze použít v deklaracích nebo definicích funkce.

- Můžete zadat **vlákno** atribut pouze na položky dat s trváním statického úložiště. To zahrnuje globální datové objekty (obojí **statické** a **extern**), místní statické objekty a statické datové členy třídy. Nelze deklarovat s automatické datové objekty **vlákno** atribut.

- Je nutné použít **vlákno** atribut pro deklarace a definice místního objektu vlákna, zda deklarace a definice objeví ve stejném souboru nebo v samostatných souborech.

- Nelze použít **vlákno** atribut jako modifikátor typu.

- Protože deklarace objektů, které používají **vlákno** atribut je povolen, tyto dva příklady jsou sémanticky ekvivalentní:

    ```cpp
    // declspec_thread_2.cpp
    // compile with: /LD
    __declspec( thread ) class B {
    public:
       int data;
    } BObject;   // BObject declared thread local.

    class B2 {
    public:
       int data;
    };
    __declspec( thread ) B2 BObject2;   // BObject2 declared thread local.
    ```

- Standard jazyka C umožňuje inicializaci objektu nebo proměnné s výrazem zahrnujícím odkaz sám na sebe, ale pouze pro nestatické objekty. Přestože jazyk C++ obvykle umožňuje takovou dynamickou inicializaci objektu s výrazem zahrnujícím odkaz sám na sebe, tento typ inicializace není povolen s místními objekty vlákna. Příklad:

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   Všimněte si, že **sizeof** výraz, který obsahuje inicializovaný objekt, nepředstavuje odkaz sám na sebe a je povolen v jazyce C a C++.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Úložiště Thread Local (TLS)](../parallel/thread-local-storage-tls.md)