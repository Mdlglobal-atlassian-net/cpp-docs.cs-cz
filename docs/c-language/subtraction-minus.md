---
title: Odčítání (-)
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
ms.openlocfilehash: 369096025a67c67775584928d1ee3264a5a10d94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480051"
---
# <a name="subtraction--"></a>Odčítání (-)

Operátor odčítání (**-**) odečte druhý operand od prvního. Oba operandy mohou být typy s plovoucí desetinnou čárkou nebo celočíselné typy, případně může být jeden operand ukazatel a druhý celé číslo.

Při odečtení dvou ukazatelů je rozdíl převeden na celočíselnou hodnotu se znaménkem vydělením rozdílu velikostí hodnoty typu, na který ukazatel odkazuje. Velikost této celočíselné hodnoty je definována typem **ptrdiff_t** ve standardním vloženém souboru STDDEF. H. Výsledek představuje počet míst paměti tohoto typu mezi dvěma adresami. Výsledkem je zaručeno smysl pro dva prvky stejného pole, jak je popsáno v [aritmetické operace ukazatele](../c-language/pointer-arithmetic.md).

Pokud celočíselná hodnota odečtena od hodnoty ukazatele, převede operátor odčítání celočíselnou hodnotu (*můžu*) pomocí vynásobení velikost hodnoty, kterou tento ukazatel odkazuje. Po převodu představuje celočíselná hodnota *můžu* pozice v paměti, kde má každá pozice délku určený typem ukazatele. Když je převedená celočíselná hodnota odečtena od hodnoty ukazatele, výsledkem je adresa paměti *můžu* pozic před původní adresou. Nový ukazatel odkazuje na hodnotu typu odkazovaného původní hodnotou ukazatele.

## <a name="see-also"></a>Viz také

[Sčítací operátory jazyka C](../c-language/c-additive-operators.md)