---
title: "Multidimenzionální Arrays (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fbc5ca61d1a45521c67426144ad5991170849230
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="multidimensional-arrays-c"></a>Vícerozměrná pole (C)
Výraz dolního indexu může mít také více dolních indexů následovně:  
  
```  
  
expression1  
[  
expression2  
] [  
expression3  
]...  
```  
  
 Výrazy dolního indexu se přiřazují zleva doprava. Krajní levé výraz dolního indexu *expression1***[***Výraz2***]**, je první vyhodnocen. Adresa, která je výsledkem přidání *expression1* a *Výraz2* forms výraz ukazatel; potom *expression3* se přidá do této ukazatele – výraz k vytvoření nové ukazatele – výraz, a tak dále, dokud se přidal poslední výraz dolního indexu. Deferenční operátor (**\***) se použijí po poslední dolního indexu výraz vyhodnocen, pokud hodnota adresy konečné ukazatele na pole zadejte (viz následující příklady).  
  
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
 [Operátor dolního indexu:](../cpp/subscript-operator.md)