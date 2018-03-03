---
title: "Omezení konstant s plovoucí desetinnou čárkou | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- constants, floating-point
- limits, floating-point constants
- floating-point numbers, floating limits
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 715f337a4c94e65641660b4becbb33d6a151d9ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="limits-on-floating-point-constants"></a>Omezení konstant s plovoucí desetinnou čárkou
**Konkrétní Microsoft**  
  
 V následující tabulce jsou uvedena omezení hodnot konstant s plovoucí desetinnou čárkou. Soubor hlaviček FLOAT.H obsahuje tyto informace.  
  
### <a name="limits-on-floating-point-constants"></a>Omezení konstant s plovoucí desetinnou čárkou  
  
|Konstanta|Význam|Hodnota|  
|--------------|-------------|-----------|  
|**FLT_DIG –**<br />**DBL_DIG –**<br />**LDBL_DIG**|Počet číslic, *q*, tak, že číslo s plovoucí desetinnou čárkou s *q* desetinných míst zaokrouhleny do reprezentace plovoucí desetinné čárky a zpět bez ztráty přesnosti.|6<br />15<br />15|  
|**FLT_EPSILON –**<br />**DBL_EPSILON –**<br />**LDBL_EPSILON**|Nejmenší kladné číslo *x*, tak, aby *x* + 1.0 není rovno hodnotě 1.0|1.192092896e-07F<br />2.2204460492503131e-016<br />2.2204460492503131e-016|  
|**FLT_GUARD**||0|  
|**FLT_MANT_DIG –**<br />**DBL_MANT_DIG –**<br />**LDBL_MANT_DIG**|Počet číslic v základ – určeného **flt_radix –** v mantisy s plovoucí desetinnou čárkou. Číselný základ je 2. Tyto hodnoty tedy představují bity.|24<br />53<br />53|  
|**FLT_MAX –**<br />**DBL_MAX –**<br />**LDBL_MAX**|Největší reprezentovatelné číslo s plovoucí desetinnou čárkou.|3.402823466e + 38F<br />1, 7976931348623158e + 308<br />1, 7976931348623158e + 308|  
|**FLT_MAX_10_EXP –**<br />**DBL_MAX_10_EXP –**<br />**LDBL_MAX_10_EXP**|Největší celé číslo takové, že číslo 10 umocněné na toto číslo je reprezentovatelné číslo s plovoucí desetinnou čárkou.|38<br />308<br />308|  
|**FLT_MAX_EXP –**<br />**DBL_MAX_EXP –**<br />**LDBL_MAX_EXP**|Maximální celočíselná hodnota tak, aby **flt_radix –** umocněné zda kód je reprezentovat číslo s plovoucí desetinnou čárkou.|128<br />1024<br />1024|  
|**FLT_MIN –**<br />**DBL_MIN –**<br />**LDBL_MIN**|Nejmenší kladná hodnota.|1.175494351e-38F<br />2.2250738585072014e-308<br />2.2250738585072014e-308|  
|**FLT_MIN_10_EXP –**<br />**DBL_MIN_10_EXP –**<br />**LDBL_MIN_10_EXP**|Nejmenší celé číslo takové, že číslo 10 umocněné na toto číslo je reprezentovatelné číslo s plovoucí desetinnou čárkou.|-37<br />-307<br />-307|  
|**FLT_MIN_EXP –**<br />**DBL_MIN_EXP –**<br />**LDBL_MIN_EXP**|Minimální záporné celé číslo tak, aby **flt_radix –** umocněné zda kód je reprezentovat číslo s plovoucí desetinnou čárkou.|-125<br />-1021<br />-1021|  
|**FLT_NORMALIZE**||0|  
|**FLT_RADIX –**<br />**_DBL_RADIX –**<br />**_LDBL_RADIX**|Základ reprezentace pomocí exponentu.|2<br />2<br />2|  
|**FLT_ROUNDS –**<br />**_DBL_ROUNDS –**<br />**_LDBL_ROUNDS**|Režim zaokrouhlování pro sčítání desetinných čísel.|1 (téměř)<br />1 (téměř)<br />1 (téměř)|  
  
 Informace v tabulce výše se mohou v budoucích implementacích lišit.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Konstanty jazyka C s plovoucí desetinnou čárkou](../c-language/c-floating-point-constants.md)