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
ms.openlocfilehash: 729e173c695db3b4970490e84bedfd441e6ff6d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344834"
---
# <a name="usual-arithmetic-conversions"></a>Obvyklé aritmetické převody

Většina operátorů jazyka C provádí převody typu za účelem převedení operandů výrazu na společný typ nebo pro prodloužení krátkých hodnot na celočíselnou velikost použitou v operacích počítače. Převody prováděné operátory jazyka C závisí na specifickém operátoru a typu operandu nebo operandů. Mnoho operátorů však provádí podobné převody na operandech integrálního a plovoucího typu. Tyto převody se označují jako "aritmetické převody". Převod hodnoty operandu na kompatibilní typ způsobí nezměně hodnoty.

Aritmetické převody, které jsou shrnuty níže, se nazývají "obvyklé aritmetické převody". Tyto kroky jsou aplikovány pouze pro binární operátory, které očekávají aritmetický typ. Účelem je poskytnout společný typ, který je také typem výsledku. Chcete-li určit, které převody skutečně probíhají, kompilátor použije následující algoritmus pro binární operace ve výrazu. Následující postup není pořadím priority.

1. Pokud je jeden operand typu `long double`, je druhý operand převeden na typ. `long double`

1. Pokud výše uvedená podmínka není splněna a jeden operand je typu **Double**, je druhý operand převeden na typ **Double**.

1. Pokud nejsou splněny výše uvedené dvě podmínky a jeden operand je typu **float**, je druhý operand převeden na typ **float**.

1. Pokud nejsou splněny výše uvedené tři podmínky (žádný z operandů není plovoucího typu), pak jsou celočíselné převody provedeny na operandech následujícím způsobem:

   - Pokud je jeden operand typu `unsigned long`, je druhý operand převeden na typ. `unsigned long`

   - Pokud výše uvedená podmínka není splněna a jeden operand je typu **Long** a druhý typ `unsigned int`, jsou oba operandy převedeny na typ. `unsigned long`

   - Pokud nejsou splněny výše uvedené dvě podmínky a jeden operand je typu **Long**, je druhý operand převeden na typ **Long**.

   - Pokud nejsou splněny výše uvedené tři podmínky a jeden operand je typu `unsigned int`, je druhý operand převeden na typ. `unsigned int`

   - Pokud není splněna žádná z výše uvedených podmínek, jsou oba operandy převedeny na `int`typ.

Následující kód ilustruje tato pravidla převodu:

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
