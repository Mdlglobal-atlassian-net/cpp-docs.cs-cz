---
title: "Operátory přírůstku a snížení předpony | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f5a6c98d53c73a6913c9ed8e63b2a1fce43b97d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="prefix-increment-and-decrement-operators"></a>Operátory přírůstku a snížení předpony
Unární operátory (`++` a  **--** ) se označují jako "předponu" přírůstek nebo snížení operátory, jakmile se zobrazí operátory zvýšení nebo snížení hodnoty před operand. Operátory přírůstku a snížení má vyšší prioritu než předpony přírůstek a snížení. Operand musí být celé číslo, číslo s plovoucí čárkou nebo ukazatel typu a musí být výraz upravitelnými l-value (výraz bez **const** atributu). Výsledkem je, l hodnota.  
  
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