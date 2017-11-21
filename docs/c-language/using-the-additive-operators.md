---
title: "Používání operátorů sčítání | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9f2bdbc6a22754587dce3cb2a4c9b2baf12a1a1f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Operátory sčítání jazyka C](../c-language/c-additive-operators.md)