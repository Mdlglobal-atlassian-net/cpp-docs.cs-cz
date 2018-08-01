---
title: Plovoucí omezení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- float.h header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a111d2ea3e8e5503754b0d9c0c1a4f69170a41c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401756"
---
# <a name="floating-limits"></a>Plovoucí omezení
**Specifické pro Microsoft**  
  
 Následující tabulka uvádí omezení hodnot konstant s plovoucí desetinnou čárkou. Tato omezení jsou také definovány v souboru standardní hlavičku \<float.h >.  
  
### <a name="limits-on-floating-point-constants"></a>Omezení konstant s plovoucí desetinnou čárkou  
  
|Konstanta|Význam|Hodnota|  
|--------------|-------------|-----------|  
|FLT_DIG DBL_DIG LDBL_DIG|Počet číslic, q, například, že číslo s plovoucí desetinnou čárkou s q desítkovými číslicemi lze zaokrouhlit na reprezentaci s plovoucí desetinnou čárkou a zpět bez ztráty přesnosti.|6 15 15|  
|FLT_EPSILON DBL_EPSILON LDBL_EPSILON|Nejmenší kladné číslo x, že x + 1,0 není roven 1,0.|1.192092896e-07F 2.2204460492503131e-016 2.2204460492503131e-016|  
|FLT_GUARD||0|  
|FLT_MANT_DIG DBL_MANT_DIG LDBL_MANT_DIG|Počet číslic v určeném konstantou FLT_RADIX v mantise s plovoucí desetinnou čárkou. Základ číselné soustavy je 2. proto tyto hodnoty určují, služba bits.|24 53 53|  
|FLT_MAX DBL_MAX LDBL_MAX|Maximální reprezentovatelné číslo s plovoucí desetinnou čárkou.|3.402823466e+38F 1.7976931348623158e+308 1.7976931348623158e+308|  
|FLT_MAX_10_EXP DBL_MAX_10_EXP LDBL_MAX_10_EXP|Maximální celočíselná hodnota tak, že číslo 10 umocněné na toto číslo je reprezentovatelné číslo s plovoucí desetinnou čárkou.|38 308 308|  
|FLT_MAX_EXP DBL_MAX_EXP LDBL_MAX_EXP|Maximální celočíselná hodnota tak, aby FLT_RADIX umocněné na toto číslo je reprezentovatelné číslo s neplovoucí desetinnou čárkou.|128 1024 1024|  
|FLT_MIN DBL_MIN LDBL_MIN|Nejmenší kladná hodnota.|1.175494351e-38F 2.2250738585072014e-308 2.2250738585072014e-308|  
|FLT_MIN_10_EXP DBL_MIN_10_EXP LDBL_MIN_10_EXP|Nejmenší celé číslo takové, že číslo 10 umocněné na toto číslo je reprezentovatelné číslo s neplovoucí desetinnou čárkou.|-37<br /><br /> -307<br /><br /> -307|  
|FLT_MIN_EXP DBL_MIN_EXP LDBL_MIN_EXP|Nejmenší celé číslo takové, FLT_RADIX umocněné na toto číslo je reprezentovatelné číslo s plovoucí desetinnou čárkou.|-125<br /><br /> -1021<br /><br /> -1021|  
|FLT_NORMALIZE||0|  
|FLT_RADIX _DBL_RADIX _LDBL_RADIX|Základ reprezentace pomocí exponentu.|2 2 2|  
|FLT_ROUNDS _DBL_ROUNDS _LDBL_ROUNDS|Režimu zaokrouhlení s plovoucí desetinnou čárkou sčítání.|1 (blízko) 1 (blízko) 1 (blízko)|  
  
> [!NOTE]
>  Informace v tabulce se může lišit v budoucích verzích tohoto produktu.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [Omezení typu Integer](../cpp/integer-limits.md)