---
title: "Konstanty datového typu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1702065a8157596d4366af31fed3f2a80d53149c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="data-type-constants"></a>Konstanty datového typu
Konstanty datového typu jsou závislé na implementaci rozsahů povolených pro integrální datové typy hodnot. Konstanty uvedené níže zadejte rozsahy pro integrální datové typy a jsou definovány v omezení. H.  
  
> [!NOTE]
>  Možnost kompilátoru /J změní výchozí `char` typ `unsigned`.  
  
|Konstanta|Hodnota|Význam|  
|--------------|-----------|-------------|  
|**SCHAR_MAX –**|127|Maximální podepsané `char` hodnota|  
|**SCHAR_MIN –**|-128|Minimální podepsané `char` hodnota|  
|**UCHAR_MAX –**|255 (0xff)|Maximální `unsigned char` hodnota|  
|**CHAR_BIT –**|8|Počet bitů`char`|  
|**USHRT_MAX –**|65535 (0xffff)|Maximální **nepodepsané prostě** hodnota|  
|**SHRT_MAX –**|32767|Maximální počet (se znaménkem) **krátké** hodnota|  
|**SHRT_MIN –**|-32768|Minimální (se znaménkem) **krátké** hodnota|  
|**UINT_MAX –**|4294967295 (0xffffffff)|Maximální `unsigned int` hodnota|  
|**ULONG_MAX –**|4294967295 (0xffffffff)|Maximální `unsigned long` hodnota|  
|**INT_MAX –**|2147483647|Maximální počet (se znaménkem) `int` hodnota|  
|**INT_MIN –**|-2147483647-1|Minimální (se znaménkem) `int` hodnota|  
|**LONG_MAX –**|2147483647|Maximální počet (se znaménkem) **dlouho** hodnota|  
|**LONG_MIN –**|-2147483647-1|Minimální (se znaménkem) **dlouho** hodnota|  
|**CHAR_MAX –**|127 (Pokud se používá možnost /J 255).|Maximální `char` hodnota|  
|**CHAR_MIN –**|-128 (0, pokud se používá možnost /J)|Minimální `char` hodnota|  
|**MB_LEN_MAX –**|2|Maximální počet bajtů v vícebajtových`char`|  
|**_I64_MAX**|9223372036854775807|Maximální (podepsaný držitelem) __**int64** hodnota|  
|**_I64_MIN**|-9223372036854775807-1|Minimální (podepsaný držitelem) __**int64** hodnota|  
|**_UI64_MAX**|0xffffffffffffffff|Maximální (bez znaménka) __**int64** hodnota|  
  
 Následující konstanty poskytnout rozsahu a dalších vlastností **dvojité** a **float** datové typy a jsou definovány v FLOAT. V:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|**DBL_DIG –**|15|počet desetinných míst přesnost|  
|**DBL_EPSILON –**|2.2204460492503131e-016|Nejmenší tak, aby 1.0 +**dbl_epsilon –** ! = 1.0|  
|**DBL_MANT_DIG –**|53|počet bitů mantisa|  
|**DBL_MAX –**|1, 7976931348623158e + 308|Maximální hodnota|  
|**DBL_MAX_10_EXP –**|308|Maximální decimal exponent|  
|**DBL_MAX_EXP –**|1024|Maximální binární exponent|  
|**DBL_MIN –**|2.2250738585072014e-308|Minimální kladnou hodnotu|  
|**DBL_MIN_10_EXP –**|(-307)|Minimální decimal exponent|  
|**DBL_MIN_EXP –**|(-1021)|Minimální binární exponent|  
|**_DBL_RADIX –**|2|Základ exponentu –|  
|**_DBL_ROUNDS –**|1|Přidání zaokrouhlení: téměř|  
|**FLT_DIG –**|6|Počet desetinných míst přesnost|  
|**FLT_EPSILON –**|1.192092896e-07F|Nejmenší tak, aby 1.0 +**flt_epsilon –** ! = 1.0|  
|**FLT_MANT_DIG –**|24|Počet bitů v mantisa|  
|**FLT_MAX –**|3.402823466e + 38F|Maximální hodnota|  
|**FLT_MAX_10_EXP –**|38|Maximální decimal exponent|  
|**FLT_MAX_EXP –**|128|Maximální binární exponent|  
|**FLT_MIN –**|1.175494351e-38F|Minimální kladnou hodnotu|  
|**FLT_MIN_10_EXP –**|(-37)|Minimální decimal exponent|  
|**FLT_MIN_EXP –**|(-125)|Minimální binární exponent|  
|**FLT_RADIX –**|2|Základ exponentu –|  
|**FLT_ROUNDS –**|1|Přidání zaokrouhlení: téměř|  
  
## <a name="see-also"></a>Viz také  
 [Globální konstanty](../c-runtime-library/global-constants.md)