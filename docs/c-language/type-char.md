---
title: Znakový typ
ms.date: 11/04/2016
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
ms.openlocfilehash: bc8d3bef85b82d5bb5c2575b3bc6c6d8a4887140
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152206"
---
# <a name="type-char"></a>Znakový typ

`char` Typ se používá k ukládání celočíselnou hodnotu členu reprezentovatelné znakové sady. Tuto hodnotu celého čísla je kód ASCII odpovídající zadanému znaku.

**Microsoft Specific**

Znak hodnoty typu `unsigned char` mají rozsah od 0 do 0xFF šestnáctkové. A **podepsané char** má rozsah 0x80 do 0x7F. Tyto rozsahy přeložit a 0 až 255 desetinné -128 do + 127 decimal, v uvedeném pořadí. Možnost kompilátoru /J změní výchozí z **podepsané** k `unsigned`.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Úložiště základních typů](../c-language/storage-of-basic-types.md)
