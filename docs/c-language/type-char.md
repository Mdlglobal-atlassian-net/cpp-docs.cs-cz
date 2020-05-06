---
title: Znakový typ
ms.date: 11/04/2016
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
ms.openlocfilehash: bc8d3bef85b82d5bb5c2575b3bc6c6d8a4887140
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345042"
---
# <a name="type-char"></a>Znakový typ

`char` Typ se používá k uložení celočíselné hodnoty členu reprezentovatelné znakové sady. Tato celočíselná hodnota je kód ASCII, který odpovídá zadanému znaku.

**Specifické pro Microsoft**

Hodnoty znaků typu `unsigned char` mají rozsah od 0 do hexadecimální hodnoty 0xFF. **Znak typu signed** má rozsah 0X80 až 0x7F. Tyto rozsahy se převádějí na 0 až 255 desetinných míst a-128 na + 127 desítkové číslo v uvedeném pořadí. Možnost kompilátoru/J změní výchozí hodnotu z **signed** na `unsigned`.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Úložiště základních typů](../c-language/storage-of-basic-types.md)
