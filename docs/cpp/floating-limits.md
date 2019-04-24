---
title: Plovoucí omezení
ms.date: 08/03/2018
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- float.h header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
ms.openlocfilehash: cead21c9a66dbc54b46b1c9f8083022a59e80295
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154398"
---
# <a name="floating-limits"></a>Plovoucí omezení

**Microsoft Specific**

Následující tabulka uvádí omezení hodnot konstant s plovoucí desetinnou čárkou. Tato omezení jsou také definovány v souboru standardní hlavičku \<float.h >.

## <a name="limits-on-floating-point-constants"></a>Omezení konstant s plovoucí desetinnou čárkou

|Konstanta|Význam|Value|
|--------------|-------------|-----------|
|`FLT_DIG`<br/>`DBL_DIG`<br/>`LDBL_DIG`|Počet číslic, q, například, že číslo s plovoucí desetinnou čárkou s q desítkovými číslicemi lze zaokrouhlit na reprezentaci s plovoucí desetinnou čárkou a zpět bez ztráty přesnosti.|6<br/>15<br/>15|
|`FLT_EPSILON`<br/>`DBL_EPSILON`<br/>`LDBL_EPSILON`|Nejmenší kladné číslo x, že x + 1,0 není roven 1,0.|1.192092896e-07F<br/>2.2204460492503131e-016<br/>2.2204460492503131e-016|
|`FLT_GUARD`||0|
|`FLT_MANT_DIG`<br/>`DBL_MANT_DIG`<br/>`LDBL_MANT_DIG`|Počet číslic v určeném konstantou `FLT_RADIX` v mantise s plovoucí desetinnou čárkou. Základ číselné soustavy je 2. proto tyto hodnoty určují, služba bits.|24<br/>53<br/>53|
|`FLT_MAX`<br/>`DBL_MAX`<br/>`LDBL_MAX`|Maximální reprezentovatelné číslo s plovoucí desetinnou čárkou.|3.402823466e + 38F<br/>1, 7976931348623158e + 308.<br/>1, 7976931348623158e + 308.|
|`FLT_MAX_10_EXP`<br/>`DBL_MAX_10_EXP`<br/>`LDBL_MAX_10_EXP`|Maximální celočíselná hodnota tak, že číslo 10 umocněné na toto číslo je reprezentovatelné číslo s plovoucí desetinnou čárkou.|38<br/>308<br/>308|
|`FLT_MAX_EXP`<br/>`DBL_MAX_EXP`<br/>`LDBL_MAX_EXP`|Maximální celočíselná hodnota tak, aby `FLT_RADIX` umocněné na toto číslo je reprezentovatelné číslo s neplovoucí desetinnou čárkou.|128<br/>1024<br/>1024|
|`FLT_MIN`<br/>`DBL_MIN`<br/>`LDBL_MIN`|Nejmenší kladná hodnota.|1.175494351e-38F<br/>2.2250738585072014e-308<br/>2.2250738585072014e-308|
|`FLT_MIN_10_EXP`<br/>`DBL_MIN_10_EXP`<br/>`LDBL_MIN_10_EXP`|Nejmenší celé číslo takové, že číslo 10 umocněné na toto číslo je reprezentovatelné číslo s neplovoucí desetinnou čárkou.|-37<br/>-307<br/>-307|
|`FLT_MIN_EXP`<br/>`DBL_MIN_EXP`<br/>`LDBL_MIN_EXP`|Nejmenší celé číslo takové, že `FLT_RADIX` umocněné na toto číslo je reprezentovatelné číslo s plovoucí desetinnou čárkou.|-125<br/>-1021<br/>-1021|
|`FLT_NORMALIZE`||0|
|`FLT_RADIX`<br/>`_DBL_RADIX`<br/>`_LDBL_RADIX`|Základ reprezentace pomocí exponentu.|2<br/>2<br/>2|
|`FLT_ROUNDS`<br/>`_DBL_ROUNDS`<br/>`_LDBL_ROUNDS`|Režimu zaokrouhlení s plovoucí desetinnou čárkou sčítání.|1 (blízko)<br/>1 (blízko)<br/>1 (blízko)|

> [!NOTE]
>  Informace v tabulce se může lišit v budoucích verzích tohoto produktu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Omezení typu Integer](../cpp/integer-limits.md)
