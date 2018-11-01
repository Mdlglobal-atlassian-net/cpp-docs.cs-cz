---
title: Převody z ostatních typů
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: f9f2d73e57c576dcf8afed008a74e5e7dd9b9d6f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448656"
---
# <a name="conversions-from-other-types"></a>Převody z ostatních typů

Protože **výčtu** hodnota je **int** hodnotu podle definice převody do a z **výčtu** hodnota jsou stejné jako u **int** typu. Kompilátor Microsoft C je celé číslo stejně jako **dlouhé**.

**Specifické pro Microsoft**

Nejsou povoleny žádné převody mezi typy struktury a sjednocení.

Jakoukoli hodnotu lze převést na typ **void**, ale výsledek takového převodu lze použít pouze v kontextu, ve kterém je hodnota výrazu zahozena, například v příkazu výrazu.

**Void** typ nemá žádnou hodnotu, podle definice. Proto jej nelze převést na libovolný typ, a dalších typů nelze převést na **void** přiřazením. Ale můžete explicitně přetypovat hodnotu na typ **void**, jak je popsáno v [převody přetypování](../c-language/type-cast-conversions.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Převody přiřazení](../c-language/assignment-conversions.md)
