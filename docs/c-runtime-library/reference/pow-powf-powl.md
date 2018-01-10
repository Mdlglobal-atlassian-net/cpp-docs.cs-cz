---
title: "Pow –, powf –, powl – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- powl
- pow
- powf
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
- powl
- pow
- _powl
- powf
dev_langs: C++
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 16a0d7beefff97eca04e5f94ab720cda4728935f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="pow-powf-powl"></a>pow, powf, powl
Vypočítá `x` umocněné z `y`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double pow(  
   double x,  
   double y   
);  
double pow(  
   double x,  
   int y  
);  // C++ only  
float pow(  
   float x,  
   float y   
);  // C++ only  
float pow(  
   float x,  
   int y  
);  // C++ only  
long double pow(  
   long double x,  
   long double y  
);  // C++ only  
long double pow(  
   long double x,  
   int y  
);  // C++ only  
float powf(  
   float x,  
   float y   
);  
long double powl(  
   long double x,  
   long double y  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Základ.  
  
 `y`  
 Exponent.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu `x` <sup>y</sup>. Žádná chybová zpráva je vytištěno na přetečení nebo podtečení.  
  
|Hodnoty x a y|Návratová hodnota pow|  
|-----------------------|-------------------------|  
|`x`\< > 0 a `y` = 0,0|1|  
|`x`= 0,0 a `y` = 0,0|1|  
|`x`= 0,0 a `y` < 0|INF|  
  
## <a name="remarks"></a>Poznámky  
 `pow`nerozpoznal celočíselné hodnoty s plovoucí desetinnou čárkou větší než 2<sup>64</sup> (například `1.0E100`).  
  
 `pow`má implementace, která používá Streaming SIMD Extensions 2 (SSE2). Informace a omezení o pomocí implementace SSE2 najdete v tématu [_set_sse2_enable –](../../c-runtime-library/reference/set-sse2-enable.md).  
  
 Protože C++ umožňuje, aby přetížení, můžete volat žádný z různých přetížení `pow`. V programu C `pow` vždy má dvě hodnoty double a vrátí hodnotu double.  
  
 `pow(int, int)` Přetížení už není k dispozici. Pokud použijete toto přetížení, kompilátor může vysílat C2668. K tomuto problému nedošlo, přetypovat první parametr `double`, `float`, nebo `long double`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`pow`, `powf`, `powl`|\<Math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_pow.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.0, y = 3.0, z;  
  
   z = pow( x, y );  
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
2.0 to the power of 3.0 is 8.0  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [Exp, expf –, expl](../../c-runtime-library/reference/exp-expf.md)   
 [protokol, logf –, log10, log10f –](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [Sqrt, sqrtf –, sqrtl –](../../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)   
 [_CIpow](../../c-runtime-library/cipow.md)