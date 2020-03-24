---
title: Příkaz výrazu
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
ms.openlocfilehash: 2f12bbbafd9be50f851e36f472098431f9ac0d5d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188997"
---
# <a name="expression-statement"></a>Příkaz výrazu

Příkazy výrazů způsobí vyhodnocení výrazů. Není proveden žádný přenos řízení nebo iterace jako výsledek příkazu výrazu.

Syntaxe pro příkaz výrazu je jednoduše

## <a name="syntax"></a>Syntaxe

```
[expression ] ;
```

## <a name="remarks"></a>Poznámky

Před provedením dalšího příkazu jsou všechny výrazy v příkazu výrazu vyhodnoceny a dokončeny všechny vedlejší účinky. Nejčastěji používané příkazy výrazů jsou přiřazení a volání funkce.  Vzhledem k tomu, že je výraz nepovinný, je samostatný středník považován za prázdný příkaz výrazu, který je označován jako příkaz [null](../cpp/null-statement.md) .

## <a name="see-also"></a>Viz také

[Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)
