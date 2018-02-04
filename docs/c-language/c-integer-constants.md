---
title: Konstanty typu Integer jazyka C | Microsoft Docs
ms.custom: 
ms.date: 02/01/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c23e90d235e1ad2a8cca577c5cfbf2be55b52b6
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2018
---
# <a name="c-integer-constants"></a>Konstanty typu Integer jazyka C

"Celočíselná konstanta" je desetinné číslo (se základem 10), osmičkové (základ 8) nebo číslo šestnáctkové (základ 16), které představuje celočíselné hodnoty. Konstanty typu integer znázornit celočíselné hodnoty, které nelze změnit.

## <a name="syntax"></a>Syntaxe

*integer-constant*:  
&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>  

*decimal-constant*:  
&nbsp;&nbsp;*nonzero-digit*  
&nbsp;&nbsp;*Decimal – konstanta* *číslice*  

*osmičkové konstanta*:  
&nbsp;&nbsp;**0**  
&nbsp;&nbsp;*osmičkové konstanta* *osmičková číslice*  

*hexadecimal-constant*:  
&nbsp;&nbsp;**0x**  *hexadecimal-digit*  
&nbsp;&nbsp;**0X**  *hexadecimal-digit*  
&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*  

*nenulové hodnoty v řádu*: jeden z  
&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**  

*osmičková číslice*: jeden z  
&nbsp;&nbsp;**0 1 2 3 4 5 6 7**  

*hexadecimální číslice*: jeden z  
&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**  
&nbsp;&nbsp;**b c d e f**  
&nbsp;&nbsp;**A B C D E F**  
  
*integer-suffix*:  
&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*unsigned-suffix* *64-bit-integer-suffix*<sub>opt</sub>

*nepodepsané příponu*: jeden z  
&nbsp;&nbsp;**u U**  

*Long příponu*: jeden z  
&nbsp;&nbsp;**l L**  
  
*64-bit-celé číslo přípona*: jeden z &nbsp; &nbsp; **i64 I64**  

Konstanty typu Integer jsou kladné, pokud jsou sebou znaménkem minus (**-**). Mínus interpretována jako operátor unární aritmetické negace. (Viz [unární aritmetické operátory](../c-language/unary-arithmetic-operators.md) informace o tento operátor.)

Pokud začíná celočíselná konstanta **0 x** nebo **0 X**, je hexadecimální. Pokud začíná číslice **0**, je osmičková. Jinak se předpokládá, být decimal.

Odpovídají následující řádky:

```C
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

Bez prázdných znaků můžete oddělit číslice celočíselná konstanta. Ukazují tyto příklady platných konstant decimal, osmičkových a šestnáctkových.

```C
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
