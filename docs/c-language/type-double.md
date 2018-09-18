---
title: Double – typ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3384c801f4ed7424711b0f51a42706650b75c41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062043"
---
# <a name="type-double"></a>Double – typ

Hodnoty s dvojitou přesností typů double mají 8 bajtů. Tento formát je podobný formátu plovoucí desetinné čárky kromě toho, že obsahuje 11bitový exponent s přesahem 1023, 52bitovou mantisu a implikovaný 1 bit vyššího řádu. Tento formát poskytuje celou řadu přibližně 1.7E-308 až 1.7E + 308 pro typ double.

**Specifické pro Microsoft**

Typ double obsahuje 64 bitů: 1 pro znaménko, 11 pro exponent a 52 pro mantisu. Jeho rozsah je +/-1.7E308 s alespoň 15 číslicemi přesnosti.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Úložiště základních typů](../c-language/storage-of-basic-types.md)