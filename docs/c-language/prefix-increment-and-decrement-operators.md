---
title: Operátory přírůstku a snížení předpony | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 116921ea46418db5c8eff3327de73a40aa42533c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="prefix-increment-and-decrement-operators"></a>Operátory přírůstku a snížení předpony
Unární operátory (`++` a **--**) se označují jako "předponu" přírůstek nebo snížení operátory, jakmile se zobrazí operátory zvýšení nebo snížení hodnoty před operand. Operátory přírůstku a snížení má vyšší prioritu než předpony přírůstek a snížení. Operand musí být celé číslo, číslo s plovoucí čárkou nebo ukazatel typu a musí být výraz upravitelnými l-value (výraz bez **const** atributu). Výsledkem je, l hodnota.  
  
 Když operátor se zobrazí před jeho operand, operand je zvýšena nebo snížena a jeho nová hodnota je výsledkem výrazu.  
  
 Operand typu integrální nebo plovoucí je zvýšena nebo snížena na celé číslo 1. Typ výsledku je stejný jako typ operandu. Operand typu ukazatele je zvýšena nebo snížena velikost objektu, který ho adresy. Body zvýšena ukazatele na další objekt; odečte ukazatel odkazuje na objekt předchozí.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje unární operátor snížení předpony:  
  
```  
if( line[--i] != '\n' )  
    return;  
```  
  
 V tomto příkladu proměnná `i` se odečte, než bude použit jako dolní index k `line`.  
  
## <a name="see-also"></a>Viz také  
 [Unární operátory jazyka C](../c-language/c-unary-operators.md)