---
title: Operátory přiřazení jazyka | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- remainder assignment operator (%=)
- '&= operator'
- bitwise-AND assignment operator
- operators [C], assignment
- operators [C], shift
- ^= operator, assignment operators
- += operator
- '>>= operator'
- '|= operator'
- division assignment operator
- subtraction operator
- right shift operators
- subtraction operator, C assignment operators
- = operator, assignment operators
- '*= operator'
- '>> operator'
- '%= operator'
- assignment operators, C
- = operator
- assignment operators
- assignment conversions
- -= operator
- multiplication assignment operator (*=)
- shift operators, right
- /= operator
- operator >>=, C assignment operators
- <<= operator
ms.assetid: 11688dcb-c941-44e7-a636-3fc98e7dac40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a13f3b36ae4f5bbd11f170d78d735427882d2ff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-assignment-operators"></a>Operátory přiřazení v jazyce C
Operátor přiřazení přiřazuje hodnotu operandu pravé strany na umístění úložiště pojmenované operandem levé strany. Operand na levé straně operace přiřazení proto musí být upravitelnou l-hodnotou. Po přiřazení má výraz přiřazení hodnotu levého operandu, není však l-hodnotou.  
  
 **Syntaxe**  
  
 *výraz přiřazení*:  
 *podmíněného výrazu*  
  
 *operátor přiřazení unární výraz přiřazení – výraz*  
  
 *operátor přiřazení*: jeden z  
 **= \*=** `/=` `%=` `+=` **-= <\<= >>= &=** `^=` `|=`  
  
 Operátory přiřazení v jazyce C mohou transformovat i přiřazovat hodnotu v jediné operaci. Jazyk C poskytuje následující operátory přiřazení:  
  
|Operátor|Provedená operace|  
|--------------|-------------------------|  
|**=**|Jednoduché přiřazení|  
|**\*=**|Přiřazení násobení|  
|`/=`|Přiřazení dělení|  
|`%=`|Zbývající přiřazení|  
|`+=`|Přiřazení sčítání|  
|**-=**|Přiřazení odčítání|  
|**<\<=**|Přiřazení posunutí doleva|  
|**>>=**|Přiřazení posunutí doprava|  
|**&=**|Přiřazení bitového operátoru AND|  
|`^=`|Přiřazení bez bitového operátoru OR|  
|`&#124;=`|Přiřazení s bitovým operátorem OR|  
  
 V přiřazení je typ hodnoty na pravé straně převeden na typ hodnoty na levé straně a hodnota je do levého operandu uložena po přiřazení. Levý operand nemůže být pole, funkce nebo konstanta. Konkrétní převod cesta, která závisí na těchto dvou typů, je podrobně popsány v části [převody typů](../c-language/type-conversions-c.md).  
  
## <a name="see-also"></a>Viz také  
 [Operátory přiřazení](../cpp/assignment-operators.md)