---
title: Výrazy v závorkách
ms.date: 11/04/2016
helpviewer_keywords:
- parentheses
- expression evaluation, evaluation order
- expressions [C++], evaluating
- parentheses, expressions
ms.assetid: b8636147-6982-408c-9e64-29e40678ee43
ms.openlocfilehash: 0b58ed2483b404df957b8e9e95e41442403036c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505544"
---
# <a name="expressions-in-parentheses"></a>Výrazy v závorkách

Libovolný operand je možné uzavřít do uvozovek, aniž by se změnil typ nebo hodnota uzavřeného výrazu. Například ve výrazu:

```
( 10 + 5 ) / 5
```

závorky kolem `10 + 5` znamenají, že hodnota `10 + 5` je vyhodnocen jako první a stane se z levého operandu rozdělení (**/**) – operátor. Výsledek `( 10 + 5 ) / 5` je 3. Bez závorek by byl výraz `10 + 5 / 5` vyhodnocen jako 11.

Přestože závorky mají vliv na způsob, jakým jsou seskupeny operandy ve výrazu, nemohou zaručit konkrétní pořadí vyhodnocení ve všech případech. Například ani závorky, ani seskupení zleva doprava v následujícím výrazu nezaručují, jaké hodnoty nabyde proměnná `i` v podřízených výrazech:

```
( i++ +1 ) * ( 2 + i )
```

Kompilátoru je umožněno vyhodnocení obou stran násobení v libovolném pořadí. Je-li počáteční hodnota proměnné `i` nula, může být celý výraz vyhodnocen jako jeden z těchto dvou příkazů:

```
( 0 + 1 + 1 ) * ( 2 + 1 )
( 0 + 1 + 1 ) * ( 2 + 0 )
```

Výjimky vyplývající z vedlejších účinků jsou popsány v [vedlejší účinky](../c-language/side-effects.md).

## <a name="see-also"></a>Viz také

[Primární výrazy jazyka C](../c-language/c-primary-expressions.md)