---
title: "Definování bloků __asm jako maker v jazyce C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af95f7b2c74d797203a0e6b3ddd6a92ddcb51e5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="defining-asm-blocks-as-c-macros"></a>Definování bloků __asm jako maker v jazyce C
**Konkrétní Microsoft**  
  
 Makra jazyka C nabízí pohodlný způsob pro vložení kódu sestavení do vašeho zdrojového kódu, ale protože makra rozšíří na jeden řádek logické vyžadují zvláštní pozornost. Chcete-li vytvořit bezproblémovou makra, postupujte podle těchto pravidel:  
  
-   Uzavřete `__asm` blokovat do složených závorek.  
  
-   Umístit `__asm` – klíčové slovo před každou instrukci sestavení.  
  
-   Pomocí starého komentáře v jazyce C ( `/* comment */`) namísto stylu sestavení komentáře ( `; comment`) nebo jeden řádek komentáře v jazyce C ( `// comment`).  
  
 Pro ilustraci, v následujícím příkladu definuje jednoduché makro:  
  
```  
#define PORTIO __asm      \  
/* Port output */         \  
{                         \  
   __asm mov al, 2        \  
   __asm mov dx, 0xD007   \  
   __asm out dx, al       \  
}  
```  
  
 Na první pohled, poslední tři `__asm` pravděpodobně nadbytečné klíčová slova. Jsou potřeba, ale protože makro rozšíří na jeden řádek:  
  
```  
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }  
```  
  
 Třetí a čtvrté `__asm` klíčová slova jsou potřeba jako oddělovače příkaz. Jediným příkazem oddělovačů rozpoznán v `__asm` znak nového řádku jsou bloky a `__asm` – klíčové slovo. Blok definován jako makra je logické jeden řádek, a proto je třeba je oddělit každou instrukci s `__asm`.  
  
 Složené závorky je také nezbytné. Pokud je vynecháte, kompilátor můžete nezaměňovat příkazy jazyka C nebo C++ na stejném řádku napravo od makro volání. Bez pravé složené závorce, kompilátor nemůže určit kde kódu sestavení zastaví a zobrazí příkazy jazyka C nebo C++ `__asm` bloku tak, jak pokyny sestavení.  
  
 Sestavení stylu komentáře, které začínají středníkem (**;**) pokračovat na konec řádku. To způsobuje problémy v makrech protože kompilátor ignoruje všechno po komentář, až na konec logického řádku. Totéž platí o jeden řádek komentáře jazyka C nebo C++ ( `// comment`). Chcete-li zabránit chybám, použijte starého komentáře v jazyce C ( `/* comment */`) v `__asm` bloky, které jsou definované jako makra.  
  
 `__asm` Blok zapsán jako makra jazyka C může trvat argumenty. Na rozdíl od běžných C makro aplikace, ale `__asm` makro nelze vrátit hodnotu. Abyste takové makra nelze používat ve výrazech jazyka C nebo C++  
  
 Dejte pozor, abyste bez vyvolání makra tohoto typu. Vyvolání makru jazyka sestavení ve funkci, například deklarovat s `__fastcall` konvence může vést k neočekávaným výsledkům. (Viz [použití a zachování registrů ve vloženém sestavení](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md).)  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vkládaný assembler](../../assembler/inline/inline-assembler.md)