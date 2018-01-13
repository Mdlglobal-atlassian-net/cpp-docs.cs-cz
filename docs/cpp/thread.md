---
title: "vlákno | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: thread_cpp
dev_langs: C++
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b26487e7f5f11bb32f418b438e9d0396b5854a91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="thread"></a>vlákno

**Konkrétní Microsoft**  
**Vlákno** modifikátor rozšířené třídy úložiště se používá k deklaraci vlákna místní proměnné. Přenosných ekvivalentní v C ++ 11 a novější, použijte [thread_local](../cpp/storage-classes-cpp.md#thread_local) specifikátor třídy úložiště pro přenosné kód. V systému Windows **thread_local** je implementováno s **__declspec(thread)**.

## <a name="syntax"></a>Syntaxe

```
__declspec( thread ) declarator
```

## <a name="remarks"></a>Poznámky

Místní úložiště vláken (TLS) je mechanismus, podle kterého všechna vlákna procesu alokují prostor pro data určitého vlákna. U standardních aplikací s více vlákny jsou data sdílena mezi všemi vlákny daného procesu, kde místní úložiště vláken představuje mechanismus pro rozdělení dat pro vlákno. Úplné informace o vláken, najdete v části [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Musíte použít deklarace lokální proměnné vláken [rozšířené syntaxe atribut](../cpp/declspec.md) a `__declspec` – klíčové slovo s **vlákno** – klíčové slovo. Například následující kód deklaruje celé číslo vlákna místní proměnné a inicializuje s hodnotou:

```cpp
__declspec( thread ) int tls_i = 1;  
```

Při použití lokální proměnné vláken v dynamicky načíst knihovny, musíte mít na paměti faktory, které můžou způsobit, že místní proměnnou, která nebyla správně inicializována:

1) Pokud je proměnná inicializována pomocí volání funkce (včetně konstruktory), tato funkce bude volat pouze pro vlákno, která způsobila, že binární/knihovny DLL pro načtení do procesu a pro tyto vláken, která spustí po binární knihovna DLL byla načtena. Funkce inicializace nejsou volat pro jiné vlákno, který byl již spuštěn, když knihovna DLL byla načtena. Dynamické inicializace proběhne volání DllMain pro DLL_THREAD_ATTACH, ale knihovnu DLL nikdy získá, které zprávy, není-li knihovnu DLL v procesu při spuštění vlákno. 

2) Místní proměnné, které jsou inicializovat staticky s konstantní hodnoty se obvykle inicializují správně na všechna vlákna. Od prosince 2017 je však známé shoda problém v Microsoft C++ compiler, při němž constexpr proměnné přijímat dynamické místo statické inicializace.  
  
   Poznámka: Oba tyto problémy se očekává v budoucnosti opraven aktualizací kompilátoru.


Kromě toho musí odpovídat tyto pokyny, když deklarace místní objekty vláken a proměnné:

- Můžete použít **vlákno** atribut pouze pro třídy a data deklarace a definice; **vlákno** nelze použít na funkce deklarace nebo definice.

- Můžete zadat **vlákno** atribut pouze na datové položky s úložiště se statickými doba trvání. To zahrnuje globální datové objekty (obojí **statické** a **extern**), místní statické objekty a členy statických dat tříd. Nelze deklarovat automatické datové objekty s **vlákno** atribut.

- Je nutné použít **vlákno** atribut deklarace a definice objekt místní vlákno, jestli deklarace a definice nastat ve stejném souboru nebo samostatné soubory.

- Nelze použít **vlákno** atribut jako typ modifikátoru.

- Protože deklarace objektů, které používají **vlákno** atribut je povoleno, tyto dva příklady jsou sémanticky ekvivalentní:

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

     Všimněte si, že **sizeof** výraz, který obsahuje inicializovaný objekt nepředstavuje odkaz sám na sebe a je povolený v C a C++.

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)  
[Klíčová slova](../cpp/keywords-cpp.md)  
[Úložiště Thread Local (TLS)](../parallel/thread-local-storage-tls.md)
