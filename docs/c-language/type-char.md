---
title: Znakový typ
ms.date: 11/04/2016
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
ms.openlocfilehash: c0524d30e19f8b54f577216a3160f721cbd2f0e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551057"
---
# <a name="type-char"></a>Znakový typ

`char` Typ se používá k ukládání celočíselnou hodnotu členu reprezentovatelné znakové sady. Tuto hodnotu celého čísla je kód ASCII odpovídající zadanému znaku.

**Specifické pro Microsoft**

Znak hodnoty typu `unsigned char` mají rozsah od 0 do 0xFF šestnáctkové. A **podepsané char** má rozsah 0x80 do 0x7F. Tyto rozsahy přeložit a 0 až 255 desetinné -128 do + 127 decimal, v uvedeném pořadí. Možnost kompilátoru /J změní výchozí z **podepsané** k `unsigned`.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Úložiště základních typů](../c-language/storage-of-basic-types.md)