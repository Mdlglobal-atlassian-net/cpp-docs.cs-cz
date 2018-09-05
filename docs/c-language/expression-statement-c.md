---
title: Výraz Statement (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73071e5cc3eef20895e4eff3bade8e37066dfd71
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765954"
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

## <a name="see-also"></a>Viz také

[Příkazy](../c-language/statements-c.md)