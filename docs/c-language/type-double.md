---
title: Double – typ
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: 43e6cc444f4d6a973fc58b5ce550e468066aca1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290729"
---
# <a name="type-double"></a>Double – typ

Hodnoty s dvojitou přesností typů double mají 8 bajtů. Tento formát je podobný formátu plovoucí desetinné čárky kromě toho, že obsahuje 11bitový exponent s přesahem 1023, 52bitovou mantisu a implikovaný 1 bit vyššího řádu. Tento formát poskytuje celou řadu přibližně 1.7E-308 až 1.7E + 308 pro typ double.

**Microsoft Specific**

Typ double obsahuje 64 bitů: 1 pro znaménko, 11 pro exponent a 52 pro mantisu. Jeho rozsah je +/-1.7E308 s alespoň 15 číslicemi přesnosti.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Úložiště základních typů](../c-language/storage-of-basic-types.md)
