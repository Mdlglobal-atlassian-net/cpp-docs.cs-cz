---
title: Unární aritmetické operátory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C], unary
- tilde (~) one's complement operator
- bitwise-complement operator
- arithmetic operators [C++], unary
- + operator, unary operators
- unary operators
- exclamation points
- ~ operator, one's complement operator
- logical negation
- '! operator, unary arithmetic operators'
ms.assetid: 78c91415-d469-499e-9dfe-4435350fd333
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07fde5da39034ff180cad5b6678f27fe8252ce10
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="unary-arithmetic-operators"></a>Unární aritmetické operátory
V následujícím seznamu jsou uvedeny operátory jazyka C unární plus, aritmetický zápor, doplněk a logická negace:  
  
|Operátor|Popis|  
|--------------|-----------------|  
|**+**|Operátor unární plus předcházející výrazu v závorkách vynutí seskupení uzavřených operací. Používá se s výrazy, které zahrnují více než jeden komutativní nebo asociativní binární operátor. Operand musí být aritmetického typu. Výsledkem je hodnota operandu. Celočíselný operand projde celočíselným povýšením. Typ výsledku je typ povýšeného operandu.|  
|**-**|Operátor aritmetické negace vytvoří zápor (dvojkový doplněk) svého operandu. Operand musí být celočíselná hodnota nebo hodnota čísla s plovoucí desetinnou čárkou. Tento operátor provádí běžné aritmetické převody.|  
|`~`|Operátor bitového doplňku (nebo bitový operátor NOT) vytvoří bitový doplněk svého operandu. Operand musí být celočíselného typu. Tento operátor provádí běžné aritmetické převody, výsledek je typem operandu po převodu.|  
|**!**|Operátor logické negace (logický operátor NOT) vytvoří hodnotu 0, pokud má jeho operand hodnotu true (nenulovou), a hodnotu 1, pokud má jeho operand hodnotu false (0). Výsledek je typu `int`. Operand musí být celočíselná hodnota, hodnota čísla s plovoucí desetinnou čárkou nebo hodnota ukazatele.|  
  
 Unární aritmetické operace u ukazatelů jsou neplatné.  
  
## <a name="examples"></a>Příklady  
 Následující příklady znázorňují unární aritmetické operátory:  
  
```  
short x = 987;  
    x = -x;  
```  
  
 V příkladu výše, nová hodnota `x` je záporná 987 nebo-987.  
  
```  
unsigned short y = 0xAAAA;  
    y = ~y;  
```  
  
 V tomto příkladu je nová hodnota přiřazená proměnné `y` jedničkový doplněk hodnoty bez znaménka 0xAAAA, tedy 0x5555.  
  
```  
if( !(x < y) )  
```  
  
 Pokud je hodnota proměnné `x` větší nebo rovna hodnotě proměnné `y`, je výsledkem výrazu hodnota 1 (true). Pokud je hodnota proměnné `x` menší než hodnota proměnné `y`, je výsledkem hodnota 0 (false).  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)