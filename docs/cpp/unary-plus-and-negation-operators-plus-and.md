---
title: "Operátory unární Plus a Negation: + a - | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs:
- C++
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12aba6e13f10d05c8559439427d2d28bcdad089d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="unary-plus-and-negation-operators--and--"></a>Unární operátory Plus a Negation: + a -
## <a name="syntax"></a>Syntaxe  
  
```  
  
+ cast-expression  
```  
  
```  
  
- cast-expression  
```  
  
## <a name="-operator"></a>+ – operátor  
 Výsledek Unární plus – operátor (**+**) je hodnota jeho operand. Operand unárního operátoru plus musí být aritmetického typu.  
  
 Pro celočíselné operandy je prováděno celočíselné povýšení. Výsledným typem je typ, na nějž byl operand povýšen. Proto výraz `+ch`, kde `ch` je typu `char`, má za výsledek typ `int`. Hodnota zůstává nezměněna. V tématu [standardní převody](standard-conversions.md) Další informace o tom, jak se provádí povýšení.  
  
## <a name="--operator"></a>- – operátor  
 Operátor unární negace (**-**) vytvoří záporné jeho operandu. Operand pro operátor unární negace musí být aritmetické typu.  
  
 Celočíselné povýšení proběhne na celočíselných operandech a výsledný typ je typ, na který je operand povýšen. V tématu [standardní převody](standard-conversions.md) Další informace o tom, jak se provádí povýšení.  
  
## <a name="microsoft-specific"></a>Microsoft konkrétní  
 Unární negace nepodepsané počty se provádí odečtením hodnoty operand z 2 ^ n, kde n je počet bitů v objektu daného typu bez znaménka. (Microsoft C++ běží u procesorů, které využívají aritmetické doplňkem. U dalších procesorů algoritmus negace se může lišit.)  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)