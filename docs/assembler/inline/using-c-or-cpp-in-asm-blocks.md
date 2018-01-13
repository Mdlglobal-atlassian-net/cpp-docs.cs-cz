---
title: "Použití jazyka C nebo C++ v blocích __asm | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inline assembly, mixing instructions with C/C++ statements
- symbols, in __asm blocks
- macros, __asm blocks
- preprocessor directives, used in __asm blocks
- type names, used in __asm blocks
- preprocessor directives
- preprocessor, directives
- constants, in __asm blocks
- comments, in __asm blocks
- typedef names, used in __asm blocks
- __asm keyword [C++], C/C++ elements in
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ab706f682372cb0a76f0d3283157d4da9105ed6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-c-or-c-in-asm-blocks"></a>Použití jazyka C nebo C++ v blocích __asm
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Protože vloženého sestavení pokynů můžete kombinovat s příkazy jazyka C nebo C++, můžou odkazují na proměnné jazyka C nebo C++ podle názvu a používat mnoho dalších prvků tyto jazyky.  
  
 `__asm` Bloku můžete použít následující prvky jazyka:  
  
-   Symboly, včetně popisků a názvy proměnné a funkcí  
  
-   Konstanty, včetně symbolický konstanty a `enum` členy  
  
-   Makra a preprocesor – direktivy  
  
-   Komentáře (obě  **/ \* \* /**  a  **//**  )  
  
-   Zadejte názvy (kdekoli typu MASM by právní)  
  
-   `typedef`názvy, které se obvykle používá s operátory, jako **PTR** a **typu** nebo k určení členů struktury nebo sjednocení  
  
 V rámci `__asm` blok, můžete zadat celočíselné konstanty zápis v jazyce C nebo assembleru základ – zápis (0x100 a 100 h ekvivalentní, jsou například). To umožňuje definovat (pomocí `#define`) konstanta v jazyce C a použít ho v části C nebo C++ a sestavení programu. Můžete také zadat konstanty v osmičková tak, že před jejich s 0. Například 0777 určuje osmičková konstanta.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Používání operátorů v blocích __asm](../../assembler/inline/using-operators-in-asm-blocks.md)  
  
-   [Použití jazyka C nebo C++ Symbols_in blocích __asm](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)  
  
-   [Přístup k datům jazyka C nebo C++ v blocích __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)  
  
-   [Zápis funkcí s vloženým sestavením](../../assembler/inline/writing-functions-with-inline-assembly.md)  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vkládaný assembler](../../assembler/inline/inline-assembler.md)