---
title: Příkaz výrazu (C)
ms.date: 11/04/2016
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
ms.openlocfilehash: 736ed4fbbd9f87c675c0bb9566c6c31287e77917
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233706"
---
# <a name="expression-statement-c"></a>Příkaz výrazu (C)

Při spuštění příkazu výrazu je výraz vyhodnocen dle pravidel popsaných v [výrazy a přiřazení](../c-language/expressions-and-assignments.md).

## <a name="syntax"></a>Syntaxe

*příkaz výrazu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz*<sub>optimalizované</sub> **;**

Před spuštěním dalšího příkazu jsou dokončeny všechny vedlejší účinky vyhodnocení výrazu. Prázdný příkaz výrazu je označován za nulový výraz. Zobrazit [nulový výraz](../c-language/null-statement-c.md) Další informace.

Následující příklady demonstrují příkazy výrazů.

```C
x = ( y + 3 );            /* x is assigned the value of y + 3  */
x++;                      /* x is incremented                  */
x = y = 0;                /* Both x and y are initialized to 0 */
proc( arg1, arg2 );       /* Function call returning void      */
y = z = ( f( x ) + 3 );   /* A function-call expression        */
```

V posledním výrazu (volání funkce) je hodnota výrazu zahrnujícího libovolnou hodnotu vrácenou funkcí zvýšena o hodnotu 3, a potom přiřazena do proměnných `y` a `z`.

## <a name="see-also"></a>Viz také:

[Příkazy](../c-language/statements-c.md)
