---
title: Double – typ
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: 42f8ed943fd9d034d5cae8cb057e094363b27d8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532259"
---
# <a name="type-double"></a>Double – typ

Hodnoty s dvojitou přesností typů double mají 8 bajtů. Tento formát je podobný formátu plovoucí desetinné čárky kromě toho, že obsahuje 11bitový exponent s přesahem 1023, 52bitovou mantisu a implikovaný 1 bit vyššího řádu. Tento formát poskytuje celou řadu přibližně 1.7E-308 až 1.7E + 308 pro typ double.

**Specifické pro Microsoft**

Typ double obsahuje 64 bitů: 1 pro znaménko, 11 pro exponent a 52 pro mantisu. Jeho rozsah je +/-1.7E308 s alespoň 15 číslicemi přesnosti.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Úložiště základních typů](../c-language/storage-of-basic-types.md)