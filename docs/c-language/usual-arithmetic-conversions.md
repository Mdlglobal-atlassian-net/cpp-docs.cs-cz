---
title: Obvyklé aritmetické převody
ms.date: 11/04/2016
helpviewer_keywords:
- arithmetic conversions [C++]
- type conversion [C++], arithmetic
- operators [C], arithmetic conversions
- data type conversion [C++], arithmetic
- conversions [C++], arithmetic
- arithmetic operators [C++], type conversions
ms.assetid: bfa49803-0efd-45d0-b987-111412a140d7
ms.openlocfilehash: a3a645009b9c848fc48f4dc49819ea474222b3fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540527"
---
# <a name="usual-arithmetic-conversions"></a>Obvyklé aritmetické převody

Většina operátory jazyka C provádět převody typů převést na společný typ. operandy výrazu nebo rozšiřovat krátký hodnot použitých v operacích počítač velikosti celého čísla. Převody prováděné operátory jazyka C jsou závislé na konkrétní operátor a typu operandu či operandů. Ale mnoho operátorů převodů podobně jako u operandů typu s plovoucí desetinnou čárkou a celočíselné typy. Tyto převody jsou označovány jako "aritmetické převody". Převod hodnoty operandu kompatibilní typ způsobí ignorování jakýchkoli změn na jeho hodnotu.

Aritmetické převody shrnuté níž jsou označovány jako "obvyklé aritmetické převody." Tyto kroky se použijí pouze pro binární operátory, které očekávají aritmetického typu. Účelem je poskytovat společný typ, který je také typ výsledku. Pokud chcete zjistit, které převody skutečně proběhnout, kompilátor platí následující požadovaný algoritmus pro binární operace ve výrazu. Následující postup nejsou pořadí priority.

1. Pokud některý operand je typu `long double`, je druhý operand je převeden na typ `long double`.

1. Pokud výše uvedené podmínka není splněna a některý operand je typu **double**, je druhý operand je převeden na typ **double**.

1. Pokud nejsou splněny obě uvedené podmínky a některý operand je typu **float**, je druhý operand je převeden na typ **float**.

1. Nejsou-li výše uvedené tři podmínky splněny (žádný z operandů jsou typy s plovoucí desetinnou čárkou), pak jsou prováděny celočíselné převody na operandy následujícím způsobem:

   - Pokud některý operand je typu `unsigned long`, je druhý operand je převeden na typ `unsigned long`.

   - Pokud výše uvedené podmínka není splněna a některý operand je typu **dlouhé** a druhý operand typu `unsigned int`, jsou oba operandy převedeny na typ `unsigned long`.

   - Pokud nejsou splněny obě uvedené podmínky a některý operand je typu **dlouhé**, je druhý operand je převeden na typ **dlouhé**.

   - Pokud nejsou splněny výše uvedených tří podmínek a některý operand je typu `unsigned int`, je druhý operand je převeden na typ `unsigned int`.

   - Pokud jsou splněna žádná z předchozích podmínek, jsou oba operandy převedeny na typ `int`.

Následující kód znázorňuje tato pravidla převodu:

```
float   fVal;
double  dVal;
int   iVal;
unsigned long ulVal;

dVal = iVal * ulVal; /* iVal converted to unsigned long
                      * Uses step 4.
                      * Result of multiplication converted to double
                      */
dVal = ulVal + fVal; /* ulVal converted to float
                      * Uses step 3.
                      * Result of addition converted to double
                      */
```

## <a name="see-also"></a>Viz také

[Operátory jazyka C](../c-language/c-operators.md)