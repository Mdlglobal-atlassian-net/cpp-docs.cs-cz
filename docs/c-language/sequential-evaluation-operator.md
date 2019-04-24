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

Operátor sekvenčního vyhodnocení, také nazývané "operátor čárka," vyhodnotí své dva operandy postupně zleva doprava.

## <a name="syntax"></a>Syntaxe

*výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz* **,** *výrazu přiřazení*

Operátor sekvenčního vyhodnocení levý operand je vyhodnocen jako `void` výrazu. Výsledek operace má stejnou hodnotu a typ jako pravý operand. Každý operand může být libovolného typu. Operátor sekvenčního vyhodnocení neprovádí převodech typů mezi jeho operandy a nevydává l hodnotou. Po prvním operandem, což znamená, že před zahájením vyhodnocení pravého operandu jsou dokončeny všechny vedlejší účinky vyhodnocení levý operand je bod sekvence. Zobrazit [body sekvence](../c-language/c-sequence-points.md) Další informace.

Operátor sekvenčního vyhodnocení se obvykle používá k vyhodnocení dvě nebo více výrazů v kontextech kde je povolen pouze jeden výraz.

Čárky lze použít jako oddělovače v některých kontextech. Však musí být pozor, abyste nezaměnili použití čárky jako oddělovače s jejím použitím jako operátoru; Tato dvě použití jsou zcela odlišná.

## <a name="example"></a>Příklad

Tento příklad ukazuje operátor sekvenčního vyhodnocení:

```
for ( i = j = 1; i + j < 20; i += i, j-- );
```

V tomto příkladu každý operand **pro** příkazu třetí výraz je vyhodnocen nezávisle na sobě. Levý operand `i += i` je Vyhodnocená první; pravý operand `j--`, je vyhodnocen.

```
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

Ve volání funkce do `func_one`, jsou předány tři argumenty oddělené čárkami: `x`, `y + 2`, a `z`. Ve volání funkce `func_two` donutí závorky kompilátor interpretovat první čárku jako operátor sekvenčního vyhodnocení. Toto volání funkce předává do funkce `func_two` dva argumenty. Prvním argumentem je výsledek operace sekvenčního vyhodnocení `(x--, y + 2)`, který má hodnotu a typ výrazu `y + 2`, druhým argumentem je proměnná `z`.

## <a name="see-also"></a>Viz také:

[Operátor čárka: ,](../cpp/comma-operator.md)
