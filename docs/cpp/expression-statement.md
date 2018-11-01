---
title: Příkaz výrazu
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
ms.openlocfilehash: 2973c3e0a1cd59edfc7ef1e771454b780da23cf9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562445"
---
# <a name="expression-statement"></a>Příkaz výrazu

Příkazy výrazů způsobí vyhodnocení výrazů. Není proveden žádný přenos řízení nebo iterace jako výsledek příkazu výrazu.

Syntaxe pro příkaz výrazu je jednoduše

## <a name="syntax"></a>Syntaxe

```
[expression ] ;
```

## <a name="remarks"></a>Poznámky

Před provedením dalšího příkazu jsou všechny výrazy v příkazu výrazu vyhodnoceny a dokončeny všechny vedlejší účinky. Nejčastěji používané příkazy výrazů jsou přiřazení a volání funkce.  Jelikož je výraz nepovinný, je samotný středník považován za prázdný příkaz výrazu, označuje jako [null](../cpp/null-statement.md) příkazu.

## <a name="see-also"></a>Viz také:

[Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)