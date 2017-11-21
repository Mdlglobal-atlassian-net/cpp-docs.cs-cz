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
ms.openlocfilehash: 7d81cd7e569cd2baa8ab50b1904fa3ac15b36d0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="thread"></a>vlákno

**Konkrétní Microsoft**  
**Vlákno** modifikátor rozšířené třídy úložiště se používá k deklaraci vlákna místní proměnné. Přenosných ekvivalentní v C ++ 11 a novější, použijte [thread_local](../cpp/storage-classes-cpp.md#thread_local) specifikátor třídy úložiště.

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

Tyto pokyny je nutné při deklarování místních objektů a proměnných vlákna dodržovat:

- Můžete použít **vlákno** atribut pouze pro třídy a data deklarace a definice; **vlákno** nelze použít na funkce deklarace nebo definice.

- Použití **vlákno** mohou ovlivňovat atribut [zpoždění načítání](../build/reference/linker-support-for-delay-loaded-dlls.md) knihovny DLL importuje.

- V systémech XP **vlákno** nemusí fungovat správně, pokud knihovnu DLL používá __declspec(thread) data a že je načtený dynamicky prostřednictvím LoadLibrary.

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
[Lokální úložiště vláken (TLS)](../parallel/thread-local-storage-tls.md)
