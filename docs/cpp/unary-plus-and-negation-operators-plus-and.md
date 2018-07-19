---
title: 'Operátory unární Plus a Negation: + a - | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa500288ec4982ca4e1d304fac2cd577d58f4207
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947714"
---
# <a name="unary-plus-and-negation-operators--and--"></a>Unární operátory Plus a Negation: + a -
## <a name="syntax"></a>Syntaxe  
  
```  
  
+ cast-expression  
- cast-expression  
```  
  
## <a name="-operator"></a>+ – operátor  
 Výsledek unárního operátoru plus (**+**) je hodnota jeho operandu. Operand unárního operátoru plus musí být aritmetického typu.  
  
 Pro celočíselné operandy je prováděno celočíselné povýšení. Výsledným typem je typ, na nějž byl operand povýšen. Proto výraz `+ch`, kde `ch` je typu **char**, výsledek typ **int**; hodnota zůstává nezměněna. Zobrazit [standardní převody](standard-conversions.md) Další informace o tom, jak je povýšení provedeno.  
  
## <a name="--operator"></a>- – operátor  
 Operátor unární negace (**-**) vytvoří zápor svého operandu. Operand operátoru unární negace musí být aritmetického typu.  
  
 Celočíselné povýšení proběhne na celočíselných operandech a výsledný typ je typ, na který je operand povýšen. Zobrazit [standardní převody](standard-conversions.md) Další informace o jak se provádí na podporu.  
  
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Unární negace bez znaménka se provádí tak, že se hodnota operandu od 2 ^ n, kde n je počet bitů v objektu daného typu bez znaménka.
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
