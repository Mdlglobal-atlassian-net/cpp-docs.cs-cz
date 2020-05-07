---
title: Převody z ostatních typů
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: f9f2d73e57c576dcf8afed008a74e5e7dd9b9d6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312463"
---
# <a name="conversions-from-other-types"></a>Převody z ostatních typů

Vzhledem k tomu, že hodnota **výčtu** **je celočíselná** hodnota podle definice, jsou převody na a z hodnoty **výčtu** stejné jako pro typ **int** . Pro kompilátor jazyka Microsoft C je celé číslo stejné jako **Long**.

**Specifické pro Microsoft**

Nejsou povoleny žádné převody mezi typy struktury a sjednocení.

Libovolná hodnota může být převedena na typ **void**, ale výsledek takového převodu lze použít pouze v kontextu, kde je hodnota výrazu zahozena, například v příkazu výrazu.

Typ **void** nemá v definici žádnou hodnotu. Proto jej nelze převést na žádný jiný typ a jiné typy nelze převést na typ **void** podle přiřazení. Můžete však explicitně přetypovat hodnotu na typ **void**, jak je popsáno v tématu [převody přetypování](../c-language/type-cast-conversions.md).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Převody přiřazení](../c-language/assignment-conversions.md)
