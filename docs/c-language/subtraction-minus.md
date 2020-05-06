---
title: Odčítání (-)
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
ms.openlocfilehash: 5c9510cf3708ef049b5dac213fa3de894fcd4a07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157757"
---
# <a name="subtraction--"></a>Odčítání (-)

Operátor odčítání (**-**) odečte druhý operand od prvního. Oba operandy mohou být typy s plovoucí desetinnou čárkou nebo celočíselné typy, případně může být jeden operand ukazatel a druhý celé číslo.

Při odečtení dvou ukazatelů je rozdíl převeden na celočíselnou hodnotu se znaménkem vydělením rozdílu velikostí hodnoty typu, na který ukazatel odkazuje. Velikost integrální hodnoty je definována typem **ptrdiff_t** ve standardním vloženém souboru STDDEF. Y. Výsledek představuje počet míst paměti tohoto typu mezi dvěma adresami. Výsledek je zaručen pouze jako smysluplný pro dva prvky stejného pole, jak je popsáno v tématu [aritmetický ukazatel](../c-language/pointer-arithmetic.md).

Pokud je celočíselná hodnota odečtena od hodnoty ukazatele, převede operátor odčítání celočíselnou hodnotu (*i*) tak, že ji vynásobí velikostí hodnoty, na kterou ukazatel odkazuje. Po převodu celočíselná *hodnota představuje pozici* v paměti, kde každá pozice má délku určenou typem ukazatele. Když je převedená celočíselná hodnota odečtena od hodnoty ukazatele, výsledkem je adresa paměti *i* pozice před původní adresou. Nový ukazatel odkazuje na hodnotu typu odkazovaného původní hodnotou ukazatele.

## <a name="see-also"></a>Viz také

[Operátory sčítání jazyka C](../c-language/c-additive-operators.md)
