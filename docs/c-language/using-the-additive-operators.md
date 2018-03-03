---
title: "Používání operátorů sčítání | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94e2a63412e4fecd5f358659cc4bf02f90df57ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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