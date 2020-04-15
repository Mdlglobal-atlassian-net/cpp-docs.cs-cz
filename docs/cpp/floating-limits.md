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
ms.openlocfilehash: ccd395eef319e57cecffad8a5278b6df1397f4cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373367"
---
# <a name="floating-limits"></a>Plovoucí omezení

**Specifické pro Microsoft**

V následující tabulce jsou uvedeny limity hodnot konstant s plovoucí desetinnou tázkem. Tyto limity jsou také definovány \<ve standardním souboru záhlaví float.h>.

## <a name="limits-on-floating-point-constants"></a>Omezení konstant s plovoucí desetinnou čárkou

|Trvalé|Význam|Hodnota|
|--------------|-------------|-----------|
|`FLT_DIG`<br/>`DBL_DIG`<br/>`LDBL_DIG`|Počet číslic, q, tak, že číslo s plovoucí desetinnou čárkou s q desetinné číslice mohou být zaokrouhleny do reprezentace s plovoucí desetinnou čárkou a zpět bez ztráty přesnosti.|6<br/>15<br/>15|
|`FLT_EPSILON`<br/>`DBL_EPSILON`<br/>`LDBL_EPSILON`|Nejmenší kladné číslo x, tak, aby x + 1.0 se nerovnalo 1,0.|1.192092896e-07F<br/>2.2204460492503131e-016<br/>2.2204460492503131e-016|
|`FLT_GUARD`||0|
|`FLT_MANT_DIG`<br/>`DBL_MANT_DIG`<br/>`LDBL_MANT_DIG`|Počet číslic v radixu `FLT_RADIX` určenév plovoucí desetinnou tázko. Radix je 2; proto tyto hodnoty určují bity.|24<br/>53<br/>53|
|`FLT_MAX`<br/>`DBL_MAX`<br/>`LDBL_MAX`|Maximální reprezentativní číslo s plovoucí desetinnou desetinnou tísní.|3.402823466e+38F<br/>1.7976931348623158e+308<br/>1.7976931348623158e+308|
|`FLT_MAX_10_EXP`<br/>`DBL_MAX_10_EXP`<br/>`LDBL_MAX_10_EXP`|Maximální celé číslo tak, že 10 zvýšené na toto číslo je reprezentativní číslo s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou.|38<br/>308<br/>308|
|`FLT_MAX_EXP`<br/>`DBL_MAX_EXP`<br/>`LDBL_MAX_EXP`|Maximální celé číslo, `FLT_RADIX` které je aktivováno na toto číslo, je reprezentativní číslo s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou.|128<br/>1024<br/>1024|
|`FLT_MIN`<br/>`DBL_MIN`<br/>`LDBL_MIN`|Nejmenší kladná hodnota.|1.175494351e-38F<br/>2.2250738585072014e-308<br/>2.2250738585072014e-308|
|`FLT_MIN_10_EXP`<br/>`DBL_MIN_10_EXP`<br/>`LDBL_MIN_10_EXP`|Minimální záporné celé číslo tak, aby 10 zvýšené na toto číslo bylo reprezentativní číslo s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou.|-37<br/>-307<br/>-307|
|`FLT_MIN_EXP`<br/>`DBL_MIN_EXP`<br/>`LDBL_MIN_EXP`|Minimální záporné celé `FLT_RADIX` číslo, které je vyvoláno na toto číslo, je reprezentativní číslo s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou.|-125<br/>-1021<br/>-1021|
|`FLT_NORMALIZE`||0|
|`FLT_RADIX`<br/>`_DBL_RADIX`<br/>`_LDBL_RADIX`|Základ reprezentace pomocí exponentu.|2<br/>2<br/>2|
|`FLT_ROUNDS`<br/>`_DBL_ROUNDS`<br/>`_LDBL_ROUNDS`|Režim zaokrouhlení pro přidání s plovoucí desetinnou desetinnou.|1 (v blízkosti)<br/>1 (v blízkosti)<br/>1 (v blízkosti)|

> [!NOTE]
> Informace v tabulce se mohou lišit v budoucích verzích produktu.

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[Limity celého čísla](../cpp/integer-limits.md)
