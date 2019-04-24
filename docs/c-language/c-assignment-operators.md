---
title: Operátory přiřazení v jazyce C
ms.date: 06/14/2018
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
ms.openlocfilehash: 5080f390d302840e9e7b349cf1c21ab618ae48db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326869"
---
# <a name="c-assignment-operators"></a>Operátory přiřazení v jazyce C

Operátor přiřazení přiřazuje hodnotu operandu pravé strany na umístění úložiště pojmenované operandem levé strany. Operand na levé straně operace přiřazení proto musí být upravitelnou l-hodnotou. Po přiřazení má výraz přiřazení hodnotu levého operandu, není však l-hodnotou.

## <a name="syntax"></a>Syntaxe

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*operátor přiřazení*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**=** **\*=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **|=**

Operátory přiřazení v jazyce C mohou transformovat i přiřazovat hodnotu v jediné operaci. Jazyk C poskytuje následující operátory přiřazení:

|Operátor|Provedená operace|
|--------------|-------------------------|
|**=**|Jednoduché přiřazení|
|**&#42;=**|Přiřazení násobení|
|**/=**|Přiřazení dělení|
|**%=**|Zbývající přiřazení|
|**+=**|Přiřazení sčítání|
|**-=**|Přiřazení odčítání|
|**<\<=**|Přiřazení posunutí doleva|
|**>>=**|Přiřazení posunutí doprava|
|**&=**|Přiřazení bitového operátoru AND|
|**^=**|Přiřazení bez bitového operátoru OR|
|**&#124;=**|Přiřazení s bitovým operátorem OR|

V přiřazení je typ hodnoty na pravé straně převeden na typ hodnoty na levé straně a hodnota je do levého operandu uložena po přiřazení. Levý operand nemůže být pole, funkce nebo konstanta. Specifická cesta přiřazení, která závisí na dvou typech, je podrobně popsána v [převody typů](../c-language/type-conversions-c.md).

## <a name="see-also"></a>Viz také:

- [Operátory přiřazení](../cpp/assignment-operators.md)