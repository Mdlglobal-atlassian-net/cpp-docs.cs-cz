---
title: "tgamma – tgammaf –, tgammal | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- tgamma
- tgammaf
- tgammal
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
dev_langs: C++
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fefaaaf6dd6e660c4cda53d28194d6052d1d8bf4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal
Určuje funkce gamma zadané hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double tgamma(  
   double x  
);  
  
float tgamma(  
   float x  
); //C++ only  
  
long double tgamma(  
   long double x  
); //C++ only  
  
float tgammaf(  
   float x  
);  
  
long double tgammal(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`x`  
 Hodnota k vyhledání gama z.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí gama z `x`.  
  
 Rozsah chybě může dojít, pokud odhad `x` je příliš velký či příliš malý pro datový typ. Chyba domény nebo rozsah chybě může dojít, pokud `x` < = 0.  
  
|Problém|Vrátí|  
|-----------|------------|  
|x = ±0|±INFINITY|  
|x = záporné celé číslo|NaN|  
|x = - INFINITY|NaN|  
|x = + INFINITY|+ INFINITY|  
|x = NaN.|NaN|  
|chyby domény|NaN|  
|Chyba pólu|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|  
|Rozsah chybu přetečení|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|  
|Podtečení rozsah chyby|správnou hodnotu, po zaokrouhlení.|  
  
 Vznikly chyby uvedené v [_matherr –](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení tgamma –, které provádějí a vrátí float a typy long double. V programu C tgamma – vždy provede a vrátí hodnotu typu double.  
  
 Pokud x je číslo přirozený, vrátí tato funkce faktoriál (x-1).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`tgamma`,                `tgammaf`,  `tgammal`|\<Math.h >|\<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [lgamma, lgammaf, lgammal](../../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)