---
title: "Plovoucí omezení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb5257b9b70750172a79b4c22a7da6c728664807
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="floating-limits"></a>Plovoucí omezení
**Konkrétní Microsoft**  
  
 Následující tabulka uvádí omezení pro hodnoty konstant s plovoucí desetinnou čárkou. Tyto limity, je definována v souboru standardní hlavičku FLOAT. H.  
  
### <a name="limits-on-floating-point-constants"></a>Omezení konstant s plovoucí desetinnou čárkou  
  
|Konstanta|Význam|Hodnota|  
|--------------|-------------|-----------|  
|FLT_DIG – DBL_DIG – LDBL_DIG|Počet číslic, otázky, tak, že můžete do reprezentace plovoucí desetinné čárky a zpět bez ztráty přesnost zaokrouhlen číslo s plovoucí desetinnou čárkou s q desetinných míst.|6 15 15|  
|FLT_EPSILON – DBL_EPSILON – LDBL_EPSILON|Nejmenší kladné číslo x tak, že hodnota x + 1.0 není rovno hodnotě 1.0.|1.192092896e-07F 2.2204460492503131e-016 2.2204460492503131e-016|  
|FLT_GUARD||0|  
|FLT_MANT_DIG – DBL_MANT_DIG – LDBL_MANT_DIG|Počet číslic v základ – určeného flt_radix – v mantisy s plovoucí desetinnou čárkou. Základ – je 2; proto tyto hodnoty zadat bits.|24 53 53|  
|FLT_MAX – DBL_MAX – LDBL_MAX|Maximální reprezentovat číslo s plovoucí desetinnou čárkou.|3.402823466e+38F 1.7976931348623158e+308 1.7976931348623158e+308|  
|FLT_MAX_10_EXP – DBL_MAX_10_EXP – LDBL_MAX_10_EXP|Maximální celočíselná hodnota tak, aby 10 umocněné toto číslo je reprezentovat číslo s plovoucí desetinnou čárkou.|38 308 308|  
|FLT_MAX_EXP – DBL_MAX_EXP – LDBL_MAX_EXP|Maximální celočíselná hodnota tak, aby flt_radix – umocněné toto číslo je reprezentovat číslo plovoucí čárkou.|128 1024 1024|  
|FLT_MIN – DBL_MIN – LDBL_MIN|Nejmenší kladná hodnota.|1.175494351e-38F 2.2250738585072014e-308 2.2250738585072014e-308|  
|FLT_MIN_10_EXP – DBL_MIN_10_EXP – LDBL_MIN_10_EXP|Minimální záporné celé číslo tak, aby 10 umocněné toto číslo je reprezentovat číslo plovoucí čárkou.|-37<br /><br /> -307<br /><br /> -307|  
|FLT_MIN_EXP – DBL_MIN_EXP – LDBL_MIN_EXP|Minimální záporné celé číslo tak, aby flt_radix – umocněné toto číslo je reprezentovat číslo s plovoucí desetinnou čárkou.|-125<br /><br /> -1021<br /><br /> -1021|  
|FLT_NORMALIZE||0|  
|FLT_RADIX – _DBL_RADIX – _LDBL_RADIX|Základ reprezentace pomocí exponentu.|2 2 2|  
|FLT_ROUNDS – _DBL_ROUNDS – _LDBL_ROUNDS|Zaokrouhlení režim pro přidání s plovoucí desetinnou čárkou.|1 (blízko) 1 (blízko) 1 (blízko)|  
  
> [!NOTE]
>  Informace v tabulce se můžou lišit v budoucích verzích produktu.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Omezení typu Integer](../cpp/integer-limits.md)