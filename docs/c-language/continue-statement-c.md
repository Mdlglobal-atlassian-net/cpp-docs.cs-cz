---
title: "pokračovat Statement (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- continue
dev_langs:
- C++
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cdf4d877ef1b88826d66e36a7ce24fdcff2cb348
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="continue-statement-c"></a>continue – příkaz (C)
Příkaz `continue` předá řízení následující iteraci nejbližšího ohraničujícího příkazu `do`, `for` nebo `while`, ve kterém se zobrazí, a vynechá všechny zbývající příkazy v těle příkazu `do`, `for` nebo `while`.  
  
## <a name="syntax"></a>Syntaxe  
 `jump-statement`:  
 `continue;`  
  
 Další iterace příkazu `do`, `for` nebo `while` se určí takto:  
  
-   V rámci příkazu `do` nebo `while` začíná další iterace přehodnocením výrazu příkazu `do` nebo `while`.  
  
-   Příkaz `continue` v příkazu `for` způsobí vyhodnocení výrazu smyčky `for`. Poté kompilátor přehodnotí podmíněný výraz a podle výsledku buď ukončí, nebo provede iteraci těla příkazu. V tématu [pro příkaz](../c-language/for-statement-c.md) Další informace o `for` prohlášení a jeho terminálově nezávislých.  
  
 Zde je příklad příkazu `continue`:  
  
```  
while ( i-- > 0 )   
{  
    x = f( i );  
    if ( x == 1 )  
        continue;  
    y += x * x;  
}  
```  
  
 V tomto příkladu je tělo příkazu prováděno, dokud je proměnná `i` větší než 0. První `f(i)` je přiřazeno do proměnné `x`, když se poté proměnná `x` rovná 1, je proveden příkaz `continue`. Ostatní příkazy v těle jsou ignorovány a provádění pokračuje v horní části smyčky vyhodnocením testu smyčky.  
  
## <a name="see-also"></a>Viz také  
 [continue – příkaz](../cpp/continue-statement-cpp.md)