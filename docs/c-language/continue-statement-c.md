---
title: continue – příkaz (C)
ms.date: 11/04/2016
f1_keywords:
- continue
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
ms.openlocfilehash: 983775e6fe9887afa5784358ede1de9583b3afba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312556"
---
# <a name="continue-statement-c"></a>continue – příkaz (C)

Příkaz `continue` předá řízení následující iteraci nejbližšího ohraničujícího příkazu `do`, `for` nebo `while`, ve kterém se zobrazí, a vynechá všechny zbývající příkazy v těle příkazu `do`, `for` nebo `while`.

## <a name="syntax"></a>Syntaxe

*příkaz skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pokraeovat**

Další iterace příkazu `do`, `for` nebo `while` se určí takto:

- V rámci příkazu `do` nebo `while` začíná další iterace přehodnocením výrazu příkazu `do` nebo `while`.

- Příkaz `continue` v příkazu `for` způsobí vyhodnocení výrazu smyčky `for`. Poté kompilátor přehodnotí podmíněný výraz a podle výsledku buď ukončí, nebo provede iteraci těla příkazu. Další informace o `for` příkazu a jeho neterminálech naleznete v [příkazu for](../c-language/for-statement-c.md) .

Zde je příklad příkazu `continue`:

```
while ( i-- > 0 )
{
    x = f( i );
    if ( x == 1 )
        continue;
    y += x * x;
}
```

V tomto příkladu je tělo příkazu prováděno, dokud je proměnná `i` větší než 0. První `f(i)` je přiřazeno do proměnné `x`, když se poté proměnná `x` rovná 1, je proveden příkaz `continue`. Ostatní příkazy v těle jsou ignorovány a provádění pokračuje v horní části smyčky vyhodnocením testu smyčky.

## <a name="see-also"></a>Viz také

[Continue – příkaz](../cpp/continue-statement-cpp.md)
