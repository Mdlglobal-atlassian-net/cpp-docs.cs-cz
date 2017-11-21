---
title: Konstanty typu Integer jazyka C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 20025ae47491084436864481357125e741ccc486
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-integer-constants"></a>Konstanty typu Integer jazyka C
"Celočíselná konstanta" je desetinné číslo (se základem 10), osmičkové (základ 8) nebo číslo šestnáctkové (základ 16), které představuje celočíselné hodnoty. Konstanty typu integer znázornit celočíselné hodnoty, které nelze změnit.  
  
## <a name="syntax"></a>Syntaxe  
 *celočíselná konstanta*:  
 *Decimal – konstanta celé číslo přípona* opt  
  
 *celé číslo přípona osmičková konstanta* opt  
  
 *celé číslo přípona hexadecimální konstanta* opt  
  
 *Decimal – konstanta*:  
 *nenulové hodnoty číslice*  
  
 *číslic desetinných – konstanta*  
  
 *osmičkové konstanta*:  
 **0**  
  
 *osmičkové konstanta osmičková číslice*  
  
 *hexadecimální konstanta*:  
 **0 x***šestnáctková číslice*   
  
 **0 X***šestnáctková číslice*   
  
 *hexadecimální číslice hexadecimální – konstanta*  
  
 *nenulové hodnoty v řádu*: jeden z  
 **1 2 3 4 5 6 7 8 9**  
  
 *osmičková číslice*: jeden z  
 **0 1 2 3 4 5 6 7**  
  
 *hexadecimální číslice*: jeden z  
 **0 1 2 3 4 5 6 7 8 9**  
  
 **b c d e f**  
  
 **A B C D E F**  
  
 *celé číslo příponu*:  
 *long přípona nepodepsané příponu* opt  
  
 *přípona dlouho bez znaménka přípona* opt  
  
 *nepodepsané příponu*: jeden z  
 **u U**  
  
 *Long příponu*: jeden z  
 **l L**  
  
 *64bitové celé číslo přípona*:  
 **I64**  
  
 Konstanty typu Integer jsou kladné, pokud jsou sebou znaménkem minus (**-**). Mínus interpretována jako operátor unární aritmetické negace. (Viz [unární aritmetické operátory](../c-language/unary-arithmetic-operators.md) informace o tento operátor.)  
  
 Pokud začíná celočíselná konstanta **0 x** nebo **0 X**, je hexadecimální. Pokud začíná číslice **0**, je osmičková. Jinak se předpokládá, být decimal.  
  
 Odpovídají následující řádky:  
  
```  
0x1C   /* = Hexadecimal representation for decimal 28 */  
034    /* = Octal representation for decimal 28 */  
```  
  
 Bez prázdných znaků můžete oddělit číslice celočíselná konstanta. Ukazují tyto příklady platných konstant decimal, osmičkových a šestnáctkových.  
  
```  
/* Decimal Constants */  
10  
132  
32179  
  
/* Octal Constants */  
012  
0204  
076663  
  
/* Hexadecimal Constants */  
0xa or 0xA  
0x84  
0x7dB3 or 0X7DB3  
```  
  
## <a name="see-also"></a>Viz také  
 [Konstanty jazyka C](../c-language/c-constants.md)