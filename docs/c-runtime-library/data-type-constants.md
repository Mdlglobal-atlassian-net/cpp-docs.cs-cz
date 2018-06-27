---
title: Konstanty datového typu | Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- FLT_MIN
- SHRT_MAX
- CHAR_MIN
- MB_LEN_MAX
- DBL_EPSILON
- SHRT_MIN
- _FLT_RADIX
- FLT_DIG
- FLT_MAX_10_EXP
- FLT_MANT_DIG
- DBL_MAX_EXP
- SCHAR_MIN
- SCHAR_MAX
- DBL_MIN
- FLT_MIN_10_EXP
- _DBL_ROUNDS
- USHRT_MAX
- FLT_MAX_EXP
- LONG_MAX
- DBL_MAX
- DBL_DIG
- FLT_MIN_EXP
- INT_MIN
- DBL_MIN_10_EXP
- CHAR_BIT
- INT_MAX
- ULONG_MAX
- DBL_MIN_EXP
- LONG_MIN
- _FLT_ROUNDS
- DBL_MANT_DIG
- _DBL_RADIX
- CHAR_MAX
- FLT_MAX
- DBL_MAX_10_EXP
- UCHAR_MAX
- FLT_EPSILON
- UINT_MAX
- LLONG_MIN
- LLONG_MAX
- ULLONG_MAX
- _I8_MIN
- _I8_MAX
- _UI8_MAX
- _I16_MIN
- _I16_MAX
- _UI16_MAX
- _I32_MIN
- _I32_MAX
- _UI32_MAX
- _I64_MIN
- _I64_MAX
- _UI64_MAX
- _I128_MIN
- _I128_MAX
- _UI128_MAX
- SIZE_MAX
- RSIZE_MAX
- LDBL_DIG
- LDBL_EPSILON
- LDBL_HAS_SUBNORM
- LDBL_MANT_DIG
- LDBL_MAX
- LDBL_MAX_10_EXP
- LDBL_MAX_EXP
- LDBL_MIN
- LDBL_MIN_10_EXP
- LDBL_MIN_EXP
- _LDBL_RADIX
- LDBL_TRUE_MIN
- DECIMAL_DIG
dev_langs:
- C++
helpviewer_keywords:
- DBL_MAX_EXP constant
- _DBL_RADIX constant
- FLT_MIN_EXP constant
- DBL_EPSILON constant
- INT_MIN constant
- FLT_EPSILON constant
- DBL_MANT_DIG constant
- _FLT_RADIX constant
- DBL_MIN constant
- USHRT_MAX constant
- FLT_MAX_10_EXP constant
- _FLT_ROUNDS constant
- data type constants [C++]
- _DBL_ROUNDS constant
- CHAR_MAX constant
- FLT_MAX_EXP constant
- FLT_MIN constant
- CHAR_MIN constant
- FLT_MIN_10_EXP constant
- DBL_MIN_EXP constant
- SCHAR_MAX constant
- FLT_RADIX constant
- CHAR_BIT constant
- UCHAR_MAX constant
- DBL_RADIX constant
- FLT_ROUNDS constant
- LONG_MIN constant
- SHRT_MAX constant
- LONG_MAX constant
- DBL_MAX_10_EXP constant
- DBL_MIN_10_EXP constant
- INT_MAX constant
- constants [C++], data type
- ULONG_MAX constant
- FLT_DIG constant
- MB_LEN_MAX constant
- DBL_DIG constant
- SHRT_MIN constant
- DBL_MAX constant
- DBL_ROUNDS constant
- FLT_MAX constant
- UINT_MAX constant
- FLT_MANT_DIG constant
- SCHAR_MIN constant
- LLONG_MIN constant
- LLONG_MAX constant
- ULLONG_MAX constant
- _I8_MIN constant
- _I8_MAX constant
- _UI8_MAX constant
- _I16_MIN constant
- _I16_MAX constant
- _UI16_MAX constant
- _I32_MIN constant
- _I32_MAX constant
- _UI32_MAX constant
- _I64_MIN constant
- _I64_MAX constant
- _UI64_MAX constant
- _I128_MIN constant
- _I128_MAX constant
- _UI128_MAX constant
- SIZE_MAX constant
- RSIZE_MAX constant
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55690bc06ae838ad44e1d0d6f0527974b7859b94
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952463"
---
# <a name="data-type-constants"></a>Konstanty datového typu

Konstanty datového typu jsou závislé na implementaci rozsahy povoleny pro datové typy s plovoucí desetinnou čárkou a celočíselné hodnoty.

## <a name="integral-type-constants"></a>Konstanty integrálních typů

Tyto konstanty poskytují rozsahy pro integrální datové typy. Pokud chcete použít tyto konstanty, včetně hlavičky Limits.h – zdrojový soubor:

```C
#include <limits.h>
```

> [!NOTE]
> [/J](../build/reference/j-default-char-type-is-unsigned.md) – možnost kompilátoru změní výchozí **char** typ **nepodepsané**.

|Konstanta|Hodnota|Popis|
|--------------|-----------|-------------|
|**CHAR_BIT –**|8|Počet bitů **char**|
|**SCHAR_MIN –**|(-128)|Minimální podepsané **char** hodnota|
|**SCHAR_MAX**|127|Maximální podepsané **char** hodnota|
|**UCHAR_MAX**|255 (0xff)|Maximální **nepodepsané** **char** hodnota|
|**CHAR_MIN –**|(-128) (0, pokud **/J** možnost použít)|Minimální **char** hodnota|
|**CHAR_MAX –**|127 (Pokud 255 **/J** možnost použít)|Maximální **char** hodnota|
|**MB_LEN_MAX**|5|Maximální počet bajtů v vícebajtových **char**|
|**SHRT_MIN –**|-32768|Minimální podepsané **krátké** hodnota|
|**SHRT_MAX**|32767|Maximální podepsané **krátké** hodnota|
|**USHRT_MAX**|65535 (0xffff)|Maximální **nepodepsané** **krátké** hodnota|
|**INT_MIN –**|(-2147483647 - 1)|Minimální podepsané **int** hodnota|
|**INT_MAX –**|2147483647|Maximální podepsané **int** hodnota|
|**UINT_MAX**|4294967295 (0xffffffff)|Maximální **nepodepsané** **int** hodnota|
|**LONG_MIN**|(-2147483647 L - 1)|Minimální podepsané **dlouho** hodnota|
|**LONG_MAX**|2147483647L|Maximální podepsané **dlouho** hodnota|
|**ULONG_MAX**|4294967295UL (0xfffffffful)|Maximální **nepodepsané** **dlouho** hodnota|
|**LLONG_MIN**|(- 9223372036854775807LL - 1)|Minimální podepsané **dlouho** **dlouho** nebo **__int64** hodnota|
|**LLONG_MAX**|9223372036854775807LL|Maximální podepsané **dlouho** **dlouho** nebo **__int64** hodnota|
|**ULLONG_MAX**|0xffffffffffffffffull|Maximální **nepodepsané** **dlouho** **dlouho** hodnota|
|**_I8_MIN**|(- 127i8 - 1)|Minimální podepsané 8bitové hodnoty|
|**_I8_MAX**|127i8|Maximální podepsané 8bitové hodnoty|
|**_UI8_MAX**|0xffui8|Maximální hodnota 8bitové bez znaménka|
|**_I16_MIN**|(- 32767i16 - 1)|Minimální podepsané 16bitové hodnoty|
|**_I16_MAX**|32767i16|Maximální podepsané 16bitové hodnoty|
|**_UI16_MAX**|0xffffui16|Maximální hodnota 16bitové bez znaménka|
|**_I32_MIN**|(- 2147483647i32 - 1)|Minimální podepsané 32bitovou hodnotu|
|**_I32_MAX**|2147483647i32|Maximální podepsané 32bitovou hodnotu|
|**_UI32_MAX**|0xffffffffui32|Maximální hodnota 32-bit bez znaménka|
|**_I64_MIN**|(-9223372036854775807 - 1)|Minimální podepsané hodnotu 64-bit|
|**_I64_MAX**|9223372036854775807|Podepsané maximální hodnotu 64-bit|
|**_UI64_MAX**|0xffffffffffffffffui64|Maximální hodnota bez znaménka 64-bit|
|**_I128_MIN**|(- 170141183460469231731687303715884105727i128 - 1)|Minimální podepsaná hodnota 128-bit|
|**_I128_MAX**|170141183460469231731687303715884105727i128|Maximální podepsaná hodnota 128-bit|
|**_UI128_MAX**|0xffffffffffffffffffffffffffffffffui128|Maximální hodnota bez znaménka 128-bit|
|**SIZE_MAX**|stejné jako **_UI64_MAX** Pokud **_WIN64 –** je definován, nebo **uint_max –**|Velikost maximální nativní celé číslo|
|**RSIZE_MAX**|stejné jako (**SIZE_MAX** >> 1)|Velikost maximální zabezpečené knihovny celé číslo|

## <a name="floating-point-type-constants"></a>Konstanty s plovoucí desetinnou čárkou typu

Následující konstanty poskytnout rozsahu a dalších vlastností **dlouho** **dvojité**, **dvojité** a **float** datové typy. Pokud chcete použít tyto konstanty, včetně hlavičky float.h – zdrojový soubor:

```C
#include <float.h>
```

|Konstanta|Hodnota|Popis|
|--------------|-----------|-----------------|
|**DBL_DECIMAL_DIG**|17|počet desetinných míst zaokrouhlení přesnost|
|**DBL_DIG –**|15|počet desetinných míst přesnost|
|**DBL_EPSILON –**|2.2204460492503131e-016|Nejmenší tak, aby 1.0 + **dbl_epsilon –** ! = 1.0|
|**DBL_HAS_SUBNORM**|1|Podporuje typ subnormal čísla (denormal)|
|**DBL_MANT_DIG –**|53|počet bitů mantisy (mantisa)|
|**DBL_MAX –**|1, 7976931348623158e + 308|Maximální hodnota|
|**DBL_MAX_10_EXP –**|308|Maximální decimal exponent|
|**DBL_MAX_EXP –**|1024|Maximální binární exponent|
|**DBL_MIN –**|2.2250738585072014e-308|Minimální normalized kladná hodnota.|
|**DBL_MIN_10_EXP –**|(-307)|Minimální decimal exponent|
|**DBL_MIN_EXP –**|(-1021)|Minimální binární exponent|
|**_DBL_RADIX –**|2|Základ exponentu –|
|**DBL_TRUE_MIN**|4.9406564584124654e-324|Minimální hodnota kladné subnormal|
|**FLT_DECIMAL_DIG**|9|Počet desetinných míst zaokrouhlení přesnost|
|**FLT_DIG –**|6|Počet desetinných míst přesnost|
|**FLT_EPSILON –**|1.192092896e-07F|Nejmenší tak, aby 1.0 + **flt_epsilon –** ! = 1.0|
|**FLT_HAS_SUBNORM**|1|Podporuje typ subnormal čísla (denormal)|
|**FLT_MANT_DIG –**|24|Počet bitů v mantisy (mantisa)|
|**FLT_MAX –**|3.402823466e + 38F|Maximální hodnota|
|**FLT_MAX_10_EXP –**|38|Maximální decimal exponent|
|**FLT_MAX_EXP –**|128|Maximální binární exponent|
|**FLT_MIN –**|1.175494351e-38F|Minimální normalized kladná hodnota.|
|**FLT_MIN_10_EXP –**|(-37)|Minimální decimal exponent|
|**FLT_MIN_EXP –**|(-125)|Minimální binární exponent|
|**FLT_RADIX –**|2|Základ exponentu –|
|**FLT_TRUE_MIN**|1.401298464e-45F|Minimální hodnota kladné subnormal|
|**LDBL_DIG**|15|počet desetinných míst přesnost|
|**LDBL_EPSILON**|2.2204460492503131e-016|Nejmenší tak, aby 1.0 + **LDBL_EPSILON** ! = 1.0|
|**LDBL_HAS_SUBNORM**|1|Podporuje typ subnormal čísla (denormal)|
|**LDBL_MANT_DIG**|53|počet bitů mantisy (mantisa)|
|**LDBL_MAX**|1, 7976931348623158e + 308|Maximální hodnota|
|**LDBL_MAX_10_EXP**|308|Maximální decimal exponent|
|**LDBL_MAX_EXP**|1024|Maximální binární exponent|
|**LDBL_MIN**|2.2250738585072014e-308|Minimální normalized kladná hodnota.|
|**LDBL_MIN_10_EXP**|(-307)|Minimální decimal exponent|
|**LDBL_MIN_EXP**|(-1021)|Minimální binární exponent|
|**_LDBL_RADIX**|2|Základ exponentu –|
|**LDBL_TRUE_MIN**|4.9406564584124654e-324|Minimální hodnota kladné subnormal|
|**DECIMAL_DIG**|stejné jako **DBL_DECIMAL_DIG**|Výchozí (dvojité) desetinných míst zaokrouhlení přesnost|

## <a name="see-also"></a>Viz také:

[Globální konstanty](../c-runtime-library/global-constants.md)  
