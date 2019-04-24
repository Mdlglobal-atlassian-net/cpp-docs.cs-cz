---
title: Operátory jazyka C
ms.date: 06/14/2018
helpviewer_keywords:
- ternary operators
- operators [C]
- symbols, operators
- binary operators
- associativity of operators
- binary data, binary expressions
ms.assetid: 13bc4c8e-2dc9-4b23-9f3a-25064e8777ed
ms.openlocfilehash: 139eedf54ab42ddc34b5c049abfcd1c2638c5efc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326375"
---
# <a name="c-operators"></a>Operátory jazyka C

Operátory jazyka C jsou podskupinou [integrované operátory C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md).

Existují tři typy operátorů. Jednočlenný výraz sestává buď z jednočlenného operátoru uvedeného před operandem, nebo **sizeof** klíčového slova následovaného výrazem. Výrazem může být název proměnné nebo výraz přetypování. Je-li výraz výrazem přetypování, musí být uzavřen závorkami. Binární výraz se skládá ze dvou operandů spojených binárním operátorem. Ternární výraz je složen ze tří operandů spojených operátorem podmíněného výrazu.

Jazyk C obsahuje následující jednočlenné operátory:

|Symbol|Název|
|------------|----------|
|**-** **~** **!**|Operátor negace a doplňku|
|**&#42;** **&**|Operátory dereference a adresa|
|**sizeof**|Operátor velikosti|
|**+**|Jednočlenný operátor plus|
|**++** **--**|Jednočlenné operátory inkrementace a dekrementace|

Binární operátory jsou asociativní zleva doprava. Jazyk C poskytuje následující binární operátory:

|Symbol|Název|
|------------|----------|
|**&#42;** **/** **%**|Operátory násobení|
|**+** **-**|Operátory sčítání|
|**\<\<** **>>**|Operátory posunutí|
|**\<** **>** **\<=** **>=** **==** **!=**|Relační operátory|
|**&** **&#124;** **^**|Bitové operátory|
|**&&** **&#124;&#124;**|Logické operátory|
|**,**|Operátor sekvenčního vyhodnocení|

Operátor základu (**: >**), podporované v předchozích verzích nástroje kompilátor jazyka C společnosti Microsoft 16 bitů, je popsaná v [souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md).

Operátor podmíněného výrazu má nižší prioritu než binární výrazy a liší se od nich asociativitou zprava.

Výrazy s operátory obsahují také výrazy přiřazení, které používají jednočlenné nebo binární operátory přiřazení. Jednočlenné operátory přiřazení jsou přírůstek (**++**) a dekrementace (**--**) operátory; binární operátory přiřazení jsou operátor jednoduchého přiřazení (**=**) a operátory složeného přiřazení. Všechny složené operátory jsou kombinací jiného binárního operátoru s operátorem jednoduchého přiřazení.

## <a name="see-also"></a>Viz také:

- [Výrazy a přiřazení](../c-language/expressions-and-assignments.md)
