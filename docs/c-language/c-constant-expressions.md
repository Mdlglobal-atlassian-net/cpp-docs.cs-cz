---
title: Výrazy konstant v jazyce C
ms.date: 06/14/2018
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
ms.openlocfilehash: f6984c47ef8acde462a8e92e01b72ef26a61eddc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325738"
---
# <a name="c-constant-expressions"></a>Výrazy konstant v jazyce C

Konstantní výraz je vyhodnocen v době kompilace, ne doby běhu a můžou používat v jakémkoli místě lze konstantu. Konstantní výraz se musí vyhodnotit na konstantu, která je v rozsahu reprezentovatelných hodnot typu. Operandy a konstantní výraz může být celočíselné konstanty, znakové konstanty, konstanty s plovoucí desetinnou čárkou, výčtu konstant typu přetypování, **sizeof** výrazů a jiných konstantní výrazy.

## <a name="syntax"></a>Syntaxe

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR* **?** *výraz* **:** *podmíněného výrazu*

*výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz* **,** *výrazu přiřazení*

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*operátor přiřazení*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**=** **&#42;=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **&#124;=**

Neterminály deklarátor – struktura, enumerátoru, s přímým přístupem deklarátor, přímo abstraktní deklarátor a příkaz s popiskem obsahují *konstantní výraz* neterminálu.

Celočíselný konstantní výraz musí použít k určení velikosti bitového pole člena struktury, hodnota konstanty výčtu, velikost pole nebo hodnoty **případ** konstantní.

Konstantní výrazy direktivy preprocesoru jsou i další omezení. V důsledku toho jsou označovány jako "s omezeným přístupem konstantní výrazy." S omezeným přístupem konstantní výraz nemůže obsahovat **sizeof** výrazy konstanty výčtu typu přetypování na typ nebo konstanty s plovoucí desetinnou čárkou typu. Může ale obsahovat speciální konstantní výraz **definované (** _identifikátor_ **)**.

## <a name="see-also"></a>Viz také:

- [Operandy a výrazy](../c-language/operands-and-expressions.md)
