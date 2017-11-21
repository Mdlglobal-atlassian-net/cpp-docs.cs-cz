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
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f6d42bb76458833614b0a057906ca11d9f9071c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [v]`x`  
 První hodnota.  
  
 [v]`y`  
 Druhá hodnota.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí kladné rozdíl mezi `x` a `y`:  
  
|Návratová hodnota|Scénář|  
|------------------|--------------|  
|x-y|Pokud x > y|  
|0|Pokud x < = y|  
  
 Jinak může vrátit jednu z těchto chyb:  
  
|Problém|Vrátí|  
|-----------|------------|  
|Rozsah chybu přetečení|+ Huge_val – + HUGE_VALF, nebo + HUGE_VALL|  
|Podtečení rozsah chyby|správnou hodnotu (po zaokrouhlení)|  
|`x`nebo `y` je NaN.|NaN|  
  
 Vznikly chyby uvedené v [_matherr –](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `fdim` , přijmout a vrátit float a typy long double. V programu C `fdim` vždy provede a vrátí hodnotu typu double.  
  
 S výjimkou NaN zpracování, tato funkce je ekvivalentní volání `fmax(x - y, 0)`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`fdim`, `fdimf`, `fdiml`|\<Math.h >|\<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [Fmax, fmaxf –, fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)   
 [Abs, labs, llabs –, _abs64 –](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)