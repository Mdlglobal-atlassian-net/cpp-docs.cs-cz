---
title: Sčítání (+)
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
ms.openlocfilehash: 8938042b373e062e99951faa752d78632d9201bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499772"
---
# <a name="addition-"></a>Sčítání (+)

Operátor sčítání (**+**) způsobí, že mají být přidány dva operandy. Oba operandy mohou být typy s plovoucí desetinnou čárkou nebo celočíselné typy, případně může být jeden operand ukazatel a druhý celé číslo.

Při přidání celého čísla na ukazatel celočíselnou hodnotu (*můžu*) je převeden vynásobením velikostí hodnoty, kterou tento ukazatel odkazuje. Po převodu představuje celočíselná hodnota *můžu* pozice v paměti, kde má každá pozice délku určený typem ukazatele. Když je převedená celočíselná hodnota se přidá k hodnotě ukazatele, výsledkem je nová hodnota ukazatele představující adresu *můžu* pozice z původní adresou. Nová hodnota ukazatele adresuje hodnotu stejného typu jako původní hodnotou ukazatele a proto je stejný jako indexování pole (viz [One-Dimensional pole](../c-language/one-dimensional-arrays.md) a [vícerozměrná pole](../c-language/multidimensional-arrays-c.md)). Pokud součet ukazatel ukazuje mimo pole, s výjimkou první umístění za koncem vysoké, výsledek není definován. Další informace najdete v tématu [aritmetické operace ukazatele](../c-language/pointer-arithmetic.md).

## <a name="see-also"></a>Viz také

[Sčítací operátory jazyka C](../c-language/c-additive-operators.md)