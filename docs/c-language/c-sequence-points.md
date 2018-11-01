---
title: Body sekvence jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- sequence points
ms.assetid: c84885a5-4336-4eba-a643-058df4249903
ms.openlocfilehash: 995f4176c046da5d34a43860c8e8f01330aee56c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650824"
---
# <a name="c-sequence-points"></a>Body sekvence jazyka C

Mezi po sobě jdoucími "body sekvence" hodnoty objektu lze upravit pouze jednou výrazem. Jazyk C definuje následující body sekvence:

- Levý operand logického – a – operátor (**&&**). Levý operand logického-operátoru je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním proveďte. Pokud levý operand je vyhodnocen jako NEPRAVDA (0), je druhý operand, nebude hodnocen.

- Levý operand logického operátoru OR – operátor (`||`). Levý operand operátoru logický operátor OR je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním proveďte. Pokud je levý operand vyhodnocen jako true (nenulový), je druhý operand, nebude hodnocen.

- Levý operand operátoru čárky. Levý operand operátoru čárky je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním proveďte. Oba operandy operátoru čárky jsou vždy vyhodnoceny. Všimněte si, že operátor čárky ve volání funkce nezaručuje pořadí jejich vyhodnocování.

- Operátor volání funkce. Jsou vyhodnoceny všechny argumenty funkce a všechny vedlejší účinky jsou před vstupem do této funkce dokončit. Je zadán žádný pořadí vyhodnocování mezi argumenty.

- První operand podmíněného operátoru. První operand podmíněného operátoru je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním proveďte.

- Konec úplného výrazu inicializace (to znamená, výraz, který není součástí jiného výrazu, jako je konec inicializace v příkazu deklarace).

- Výraz v příkazu výrazu. Příkazy výrazů se skládají z volitelného výrazu následovaného středníkem (**;**). Tento výraz je vyhodnocen pro jeho vedlejší účinky a je bod sekvence toto vyhodnocení.

- Řídicí výraz ve výběru (**Pokud** nebo `switch`) příkaz. Výraz je zcela vyhodnocen a všechny vedlejší účinky dokončit před provedením kódu závislého na výběru.

- Řídicí výraz `while` nebo **proveďte** příkazu. Výraz je zcela vyhodnocen a všechny vedlejší účinky jsou před vykonáním jakýchkoli příkazů v další iteraci Dokončit `while` nebo **proveďte** smyčky jsou spouštěny.

- Všechny tři výrazy **pro** příkazu. Výrazy jsou zcela vyhodnocen a všechny vedlejší účinky jsou před vykonáním jakýchkoli příkazů v další iteraci Dokončit **pro** smyčky jsou spouštěny.

- Výraz v `return` příkazu. Výraz je zcela vyhodnocen a všechny vedlejší účinky dokončit dříve, než vrátí řízení volající funkci.

## <a name="see-also"></a>Viz také

[Vyhodnocení výrazu](../c-language/expression-evaluation-c.md)