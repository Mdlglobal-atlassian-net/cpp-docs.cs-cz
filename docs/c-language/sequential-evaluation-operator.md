---
title: Operátor sekvenčního vyhodnocení
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
ms.openlocfilehash: 2cbffc51fb7113ae442dbfcd1db01bbf27a67746
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158518"
---
# <a name="sequential-evaluation-operator"></a>Operátor sekvenčního vyhodnocení

Operátor sekvenčního vyhodnocení, označovaný také jako "operátor čárky", vyhodnocuje své dva operandy postupně zleva doprava.

## <a name="syntax"></a>Syntaxe

*výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz* **,** *přiřazení – výraz*

Levý operand operátoru sekvenčního vyhodnocení je vyhodnocen jako `void` výraz. Výsledek operace má stejnou hodnotu a typ jako pravý operand. Každý operand může být libovolného typu. Operátor sekvenčního vyhodnocení neprovádí převody typů mezi operandy a nevrací l-value. Po prvním operandu je sekvenční bod, což znamená, že všechny vedlejší účinky z vyhodnocení levého operandu jsou dokončeny před zahájením hodnocení pravého operandu. Další informace naleznete v části [body sekvence](../c-language/c-sequence-points.md) .

Operátor sekvenčního vyhodnocení se obvykle používá k vyhodnocení dvou nebo více výrazů v kontextech, kde je povolen pouze jeden výraz.

V některých kontextech lze použít čárky jako oddělovače. Musíte ale pečlivě Zaměňujte použití čárky jako oddělovače s jeho použitím jako operátoru. Tato dvě použití jsou zcela odlišná.

## <a name="example"></a>Příklad

Tento příklad znázorňuje operátor sekvenčního vyhodnocení:

```
for ( i = j = 1; i + j < 20; i += i, j-- );
```

V tomto příkladu je každý operand třetího výrazu příkazu **for** vyhodnocen nezávisle. Levý operand `i += i` je vyhodnocen jako první; pak je vyhodnocen pravý `j--`operand.

```
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

Ve volání `func_one`funkce jsou předány tři argumenty oddělené čárkami: `x`, `y + 2`a. `z` Ve volání funkce `func_two` donutí závorky kompilátor interpretovat první čárku jako operátor sekvenčního vyhodnocení. Toto volání funkce předává do funkce `func_two` dva argumenty. Prvním argumentem je výsledek operace sekvenčního vyhodnocení `(x--, y + 2)`, který má hodnotu a typ výrazu `y + 2`, druhým argumentem je proměnná `z`.

## <a name="see-also"></a>Viz také

[Operátor čárky:,](../cpp/comma-operator.md)
