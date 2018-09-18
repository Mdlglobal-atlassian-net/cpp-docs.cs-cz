---
title: pokračovat Statement (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- continue
dev_langs:
- C++
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bde13a20dd1b54ed8a1b4271895715596549f1a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069297"
---
# <a name="continue-statement-c"></a>continue – příkaz (C)

Příkaz `continue` předá řízení následující iteraci nejbližšího ohraničujícího příkazu `do`, `for` nebo `while`, ve kterém se zobrazí, a vynechá všechny zbývající příkazy v těle příkazu `do`, `for` nebo `while`.

## <a name="syntax"></a>Syntaxe

*příkaz-skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pokračování**

Další iterace příkazu `do`, `for` nebo `while` se určí takto:

- V rámci příkazu `do` nebo `while` začíná další iterace přehodnocením výrazu příkazu `do` nebo `while`.

- Příkaz `continue` v příkazu `for` způsobí vyhodnocení výrazu smyčky `for`. Poté kompilátor přehodnotí podmíněný výraz a podle výsledku buď ukončí, nebo provede iteraci těla příkazu. Naleznete v tématu [pro příkaz](../c-language/for-statement-c.md) Další informace o `for` příkazu a jeho neterminálech.

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

[continue – příkaz](../cpp/continue-statement-cpp.md)