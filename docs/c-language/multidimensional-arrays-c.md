---
title: Multidimenzionální Arrays (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2257ff9be5988ed6a08dd5d152c83910c6edc88
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214716"
---
# <a name="multidimensional-arrays-c"></a>Vícerozměrná pole (C)
Výraz dolního indexu může mít také více dolních indexů následovně:  
  
```  
expression1 [ expression2 ] [ expression3 ] ...  
```  
  
 Výrazy dolního indexu se přiřazují zleva doprava. Úplně vlevo výraz dolního indexu *expression1* **[** *expression2* **]**, je vyhodnocen jako první. Adresa, která je výsledkem přidání *expression1* a *expression2* tvoří výraz ukazatele; potom *expression3* se přidá k tomuto výrazu ukazatele a vytvoří nový výraz ukazatele, a tak dále, dokud se přidala posledního výrazu dolního indexu. Operátor dereference (<strong>\*</strong>) se použije po vyhodnocení posledního výrazu dolního indexu, pokud poslední ukazatel hodnotu typ pole (Další příklady naleznete níže).  
  
 Výrazy s více dolními indexy odkazují na prvky „vícerozměrných polí“. Vícerozměrné pole je pole, jehož prvky jsou pole. Například, první prvek trojrozměrného pole je dvourozměrné pole.  
  
## <a name="examples"></a>Příklady  
 Pro následující příklady je pole s názvem `prop` deklarováno se třemi prvky, každý z nich je pole 4 krát 6 hodnot typu `int`.  
  
```  
int prop[3][4][6];  
int i, *ip, (*ipp)[6];  
```  
  
 Odkaz na pole `prop` vypadá takto:  
  
```  
i = prop[0][0][1];  
```  
  
 Výše uvedený příklad ukazuje, jak odkazovat na druhý jednotlivý prvek typu `int` pole `prop`. Pole jsou uložena po řádku, takže poslední dolní index se mění nejrychleji. Výraz `prop[0][0][2]` odkazuje na další (třetí) prvek pole a tak dále.  
  
```  
i = prop[2][1][3];  
```  
  
 Tento příkaz je složitější odkaz na jednotlivý prvek pole `prop`. Výraz se vyhodnotí takto:  
  
1.  První dolní index, `2`, se vynásobí velikostí pole 4 krát 6 hodnot typu `int` a přičte se k hodnotě ukazatele `prop`. Výsledek odkazuje na třetí pole 4 krát 6 výrazu `prop`.  
  
2.  Druhý dolní index, `1`, se vynásobí velikostí pole 6 prvků typu `int` a přičte se k adrese reprezentované výrazem `prop[2]`.  
  
3.  Každý prvek 6prvkového pole je hodnota typu `int`, takže konečný dolní index, `3`, se vynásobí velikostí typu `int` před přičtením k výrazu `prop[2][1]`. Výsledný ukazatel odkazuje na čtvrtý prvek 6prvkového pole.  
  
4.  Na hodnotu ukazatele je použit operátor dereference. Výsledkem je prvek typu `int` na této adrese.  
  
 Další dva příklady zobrazují případy, kdy operátor dereference není použit.  
  
```  
ip = prop[2][1];  
  
ipp = prop[2];  
```  
  
 V prvním z těchto příkazů je výraz `prop[2][1]` platným odkazem na trojrozměrné pole `prop` odkazující na 6prvkové pole (deklarované výše). Vzhledem k tomu, že hodnota ukazatele odkazuje na pole, operátor dereference není použit.  
  
 Podobně, výsledek výrazu `prop[2]` v druhém příkazu `ipp = prop[2];` je hodnota ukazatele odkazující na dvourozměrné pole.  
  
## <a name="see-also"></a>Viz také  
 [Operátor dolního indexu: []](../cpp/subscript-operator.md)