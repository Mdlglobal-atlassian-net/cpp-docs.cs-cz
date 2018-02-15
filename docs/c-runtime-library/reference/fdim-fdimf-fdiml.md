---
title: "fdim – fdimf –, fdiml | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
dev_langs:
- C++
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60e628f84dcadf7b1e214d526981191036428042
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml
Určuje kladné rozdíl mezi hodnotami prvním a druhém.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double fdim(  
   double x,   
   double y  
);  
  
float fdim(  
   float x,   
   float y  
); //C++ only  
  
long double fdim(  
   long double x,   
   long double y  
); //C++ only  
  
float fdimf(  
   float x,   
   float y  
);  
  
long double fdiml(  
   long double x,   
   long double y  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `x`  
 První hodnota.  
  
 [in] `y`  
 Druhá hodnota.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí kladné rozdíl mezi `x` a `y`:  
  
|Návratová hodnota|Scénář|  
|------------------|--------------|  
|x-y|if x > y|  
|0|if x <= y|  
  
 Jinak může vrátit jednu z těchto chyb:  
  
|Problém|Vrátí|  
|-----------|------------|  
|Rozsah chybu přetečení|+ Huge_val – + HUGE_VALF, nebo + HUGE_VALL|  
|Podtečení rozsah chyby|správnou hodnotu (po zaokrouhlení)|  
|`x` nebo `y` je NaN.|NaN|  
  
 Vznikly chyby uvedené v [_matherr –](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `fdim` , přijmout a vrátit float a typy long double. V programu C `fdim` vždy provede a vrátí hodnotu typu double.  
  
 S výjimkou NaN zpracování, tato funkce je ekvivalentní volání `fmax(x - y, 0)`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`fdim`, `fdimf`, `fdiml`|\<math.h>|\<cmath>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmax, fmaxf, fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)   
 [abs, labs, llabs, _abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)