---
title: "Výraz Statement (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7438899eb9c1c2f17b4e74c859d454e2b69af600
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expression-statement-c"></a>Příkaz výrazu (C)
Když je proveden příkaz výrazu, je tento výraz vyhodnocen podle pravidel uvedených v [výrazy a přiřazení](../c-language/expressions-and-assignments.md).  
  
## <a name="syntax"></a>Syntaxe  
 *příkaz výrazu*:  
 *výraz* opt**;**  
  
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