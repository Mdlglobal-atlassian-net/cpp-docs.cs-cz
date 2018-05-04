---
title: Používání operátorů sčítání | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44259ef77e5f09a1723064683c6900e425eb35c0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="using-the-additive-operators"></a>Používání operátorů sčítání
Následující příklady ilustrující operátory sčítání a odčítání používají tyto deklarace:  
  
```  
int i = 4, j;  
float x[10];  
float *px;  
```  
  
 Tyto příkazy jsou stejné:  
  
```  
px = &x[4 + i];  
px = &x[4] + i;    
```  
  
 Hodnota `i` se násobí hodnotou délka **float** a přidají se do `&x[4]`. Výsledná hodnota ukazatele je adresa prvku `x[8]`.  
  
```  
j = &x[i] - &x[i-2];  
```  
  
 V tomto příkladu je adresa třetího prvku pole `x` (určená pomocí `x[i-2]`) odečtena od adresy pátého prvku pole `x` (určené pomocí `x[i]`). Rozdíl je rozdělen délkou **float**; výsledkem je hodnota celého čísla 2.  
  
## <a name="see-also"></a>Viz také  
 [Sčítací operátory jazyka C](../c-language/c-additive-operators.md)