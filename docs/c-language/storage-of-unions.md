---
title: Ukládání sjednocení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a741444aa9b0e9af1e1eb344a8ac7029127af3f9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="storage-of-unions"></a>Ukládání sjednocení
Úložiště přidružené k proměnné sjednocení je místo na disku požadované pro největšího člena sjednocení. Při uložení menšího člena sjednocení může proměnná sjednocení obsahovat nevyužitý paměťový prostor. Všichni členové jsou uloženi ve stejném paměťovém prostoru a začínají na stejné adrese. Uložená hodnota je přepsána pokaždé, když je hodnota přiřazena k jinému členu. Příklad:  
  
```  
union         /* Defines a union named x */  
{  
    char *a, b;  
    float f[20];  
} x;  
```  
  
 Členové `x` union jsou v pořadí podle jejich deklarace ukazatel na `char` hodnotu, `char` hodnota a pole **float** hodnoty. Úložiště přidělené prvku `x` je požadované místo na disku pro pole o 20 prvcích `f`, jelikož `f` je nejdelším členem sjednocení. Vzhledem k tomu, že ke sjednocení není přidružena žádná značka, jeho typ je nepojmenovaný nebo „anonymní“.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace sjednocení](../c-language/union-declarations.md)