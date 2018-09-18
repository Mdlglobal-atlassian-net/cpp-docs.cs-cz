---
title: Typ char | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eec964d9b81ee93f888bbd4152f06f6bdf51b6d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053827"
---
# <a name="type-char"></a>Znakový typ

`char` Typ se používá k ukládání celočíselnou hodnotu členu reprezentovatelné znakové sady. Tuto hodnotu celého čísla je kód ASCII odpovídající zadanému znaku.

**Specifické pro Microsoft**

Znak hodnoty typu `unsigned char` mají rozsah od 0 do 0xFF šestnáctkové. A **podepsané char** má rozsah 0x80 do 0x7F. Tyto rozsahy přeložit a 0 až 255 desetinné -128 do + 127 decimal, v uvedeném pořadí. Možnost kompilátoru /J změní výchozí z **podepsané** k `unsigned`.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Úložiště základních typů](../c-language/storage-of-basic-types.md)