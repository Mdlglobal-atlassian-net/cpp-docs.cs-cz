---
title: Body sekvence jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- sequence points
ms.assetid: c84885a5-4336-4eba-a643-058df4249903
ms.openlocfilehash: 13d6044269f60dc426a8b0b9b03463f387dfaa10
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313334"
---
# <a name="c-sequence-points"></a>Body sekvence jazyka C

Mezi po sobě jdoucími body sekvence je hodnota objektu změněna pouze jednou výrazem. Jazyk C definuje následující body sekvence:

- Levý operand logického operátoru AND (**&&**). Levý operand logického operátoru AND je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před pokračováním. Pokud je levý operand vyhodnocen jako false (0), druhý operand není vyhodnocen.

- Levý operand logického operátoru OR (`||`). Levý operand logického operátoru OR je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před pokračováním. Pokud je levý operand vyhodnocen jako true (nenulový), druhý operand není vyhodnocen.

- Levý operand operátoru čárky. Levý operand operátoru čárky je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před pokračováním. Oba operandy operátoru čárky jsou vždy vyhodnoceny. Všimněte si, že operátor čárky ve volání funkce nezaručuje pořadí vyhodnocování.

- Operátor volání funkce. Všechny argumenty funkce jsou vyhodnoceny a všechny vedlejší účinky jsou dokončeny před vstupem do funkce. Není zadáno pořadí vyhodnocování mezi argumenty.

- První operand podmíněného operátoru. První operand podmíněného operátoru je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před pokračováním.

- Konec úplného inicializačního výrazu (to znamená výraz, který není součástí jiného výrazu, jako je například konec inicializace v příkazu deklarace).

- Výraz v příkazu výrazu. Příkazy výrazu se skládají z volitelného výrazu následovaného středníkem (**;**). Výraz je vyhodnocen pro své vedlejší účinky a existuje bod sekvence, který následuje za tímto hodnocením.

- Řídicí výraz v příkazu výběr (**if** nebo `switch`). Výraz je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před provedením kódu závislého na výběru.

- Řídicí `while` **výraz příkazu or** . Výraz je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před provedením jakýchkoli příkazů v další `while` iteraci **smyčky nebo** .

- Každý ze tří výrazů příkazu **for** . Výrazy jsou zcela vyhodnoceny a všechny vedlejší účinky jsou dokončeny před všemi příkazy v další iteraci smyčky **for** .

- Výraz v `return` příkazu Výraz je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před tím, než se ovládací prvek vrátí volající funkci.

## <a name="see-also"></a>Viz také

[Vyhodnocení výrazu](../c-language/expression-evaluation-c.md)
