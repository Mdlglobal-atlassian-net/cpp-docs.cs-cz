---
title: "Použití jazyka C nebo C++ symboly v blocích __asm | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b6a39b747c8c576d148bafff19a664a95fcb43e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-c-or-c-symbols-in-asm-blocks"></a>Používání symbolů jazyka C nebo C++ v blocích __asm
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 `__asm` Bloku mohou odkazovat na žádné symbol jazyka C nebo C++ v oboru, kde se zobrazí bloku. (C a C++ symboly jsou názvy proměnných, názvy funkcí a popisky; které je, názvy, které nejsou symbolický konstanty nebo `enum` členy. Nelze volat C++ členské funkce.)  
  
 Několik omezení se vztahují na používání symbolů jazyka C a C++:  
  
-   Každý příkaz jazyka sestavení může obsahovat pouze jednu C nebo C++ symbol. Více symbolů se mohou objevit v stejné pokyn sestavení pouze s **délka**, **typ**, a **velikost** výrazy.  
  
-   Funkce, kterou se odkazuje v `__asm` bloku musí být deklarován (deklaraci) dříve v programu. Jinak, kompilátor nerozlišuje mezi názvy funkcí a popisky ve `__asm` bloku.  
  
-   `__asm` Bloku nelze použít všechny symboly C nebo C++ s píše stejně jako MASM vyhrazená slova (bez ohledu na případ). MASM vyhrazená slova obsahují instrukce názvy, například **PUSH** a zaregistrujte názvy, například serveru.  
  
-   Značky struktury a sjednocení nejsou rozpoznány v `__asm` bloky.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)