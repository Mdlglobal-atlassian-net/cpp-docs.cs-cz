---
title: Výraz Statement (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18d28cdc695ae600616d63575328eeaf171bc28c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="expression-statement-c"></a>Příkaz výrazu (C)
Když je proveden příkaz výrazu, je tento výraz vyhodnocen podle pravidel uvedených v [výrazy a přiřazení](../c-language/expressions-and-assignments.md).  
  
## <a name="syntax"></a>Syntaxe  
 *příkaz výrazu*:  
 *výraz* opt **;**  
  
 Před spuštěním dalšího příkazu jsou dokončeny všechny vedlejší účinky vyhodnocení výrazu. Prázdný příkaz výrazu je označován za nulový výraz. V tématu [The Null – příkaz](../c-language/null-statement-c.md) Další informace.  
  
 Následující příklady demonstrují příkazy výrazů.  
  
```  
x = ( y + 3 );            /* x is assigned the value of y + 3  */  
x++;                      /* x is incremented                  */  
x = y = 0;                /* Both x and y are initialized to 0 */  
proc( arg1, arg2 );       /* Function call returning void      */  
y = z = ( f( x ) + 3 );   /* A function-call expression        */  
```  
  
 V posledním výrazu (volání funkce) je hodnota výrazu zahrnujícího libovolnou hodnotu vrácenou funkcí zvýšena o hodnotu 3, a potom přiřazena do proměnných `y` a `z`.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy](../c-language/statements-c.md)