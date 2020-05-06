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

Konstantní výraz je vyhodnocen v době kompilace, nikoli v době spuštění, a lze jej použít na jakémkoli místě, které lze použít konstantou. Konstantní výraz se musí vyhodnotit na konstantu, která je v rozsahu reprezentovatelné hodnoty pro tento typ. Operandy konstantního výrazu mohou být celočíselné konstanty, znakové konstanty, konstanty s plovoucí desetinnou čárkou, výčty typu, přetypování, výrazy **sizeof** a další konstantní výrazy.

## <a name="syntax"></a>Syntaxe

*konstantní výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*podmíněný výraz*

*podmíněný výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz or* **?** *výraz* **:** *podmíněný výraz*

*výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz* **,** *přiřazení – výraz*

*výraz přiřazení*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*podmíněný výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;přiřazení *unárního výrazu* – *výraz přiřazení* *operátoru*

*Assignment-operátor*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**=****&#42;** **/=** **%=** = **+=** **-=** **&#124;** = ** \< \< ** **>>=** **&=** **^=**

Neterminály pro struktury deklarátor, Enumerator, Direct deklarátor, Direct-abstract deklarátor a Label obsahují neterminály *konstantního výrazu* .

K určení velikosti bitového pole člena struktury, hodnoty konstanty výčtu, velikosti pole nebo hodnoty konstanty **případu** je nutné použít integrální konstantní výraz.

Konstantní výrazy používané v direktivách preprocesoru se vztahují na další omezení. V důsledku toho jsou známé jako "omezené konstantní výrazy". Omezený konstantní výraz nemůže obsahovat výrazy **sizeof** , konstanty výčtu, přetypování typu na jakýkoliv typ nebo konstanty s plovoucího typu. Může však obsahovat speciální konstantní výraz konstanty **(** _identifikátor_ **)**.

## <a name="see-also"></a>Viz také

- [Operandy a výrazy](../c-language/operands-and-expressions.md)
