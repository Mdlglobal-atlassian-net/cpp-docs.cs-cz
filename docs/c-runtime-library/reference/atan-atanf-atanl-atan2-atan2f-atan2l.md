---
title: "Atan atanf –, atanl –, atan2, atan2f –, atan2l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
dev_langs:
- C++
helpviewer_keywords:
- atan function
- atanf function
- atanl function
- atan2 function
- atan2l function
- arctangent function
- trigonometric functions
- atan2f function
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5da2b1bcc38c1b41a35de30e589f9660f19f78da
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l
Vypočítá Arkus tangens `x` (`atan`, `atanf`, a `atanl`) nebo Arkus tangens `y` / `x` (`atan2`, `atan2f`, a `atan2l`).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double atan(   
   double x   
);  
float atan(  
   float x   
);  // C++ only  
long double atan(  
   long double x  
);  // C++ only  
double atan2(   
   double y,   
   double x   
);  
float atan2(  
   float y,  
   float x  
);  // C++ only  
long double atan2(  
   long double y,  
   long double x  
);  // C++ only  
float atanf(   
   float x   
);  
long double atanl(  
   long double x  
);  
float atan2f(  
   float y,  
   float x  
);  
long double atan2l(  
   long double y,  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`, `y`  
 Všechna čísla.  
  
## <a name="return-value"></a>Návratová hodnota  
 `atan` Vrátí Arkus tangens `x` v rozsahu - pí/2 do pí/2 radiánech. `atan2` Vrátí Arkus tangens `y/x` v rozsahu - pí do pí radiánech. Pokud `x` 0, `atan` vrátí hodnotu 0. Pokud oba parametry `atan2` mají hodnotu 0, funkce vrátí hodnotu 0. Všechny výsledky jsou v radiánech.  
  
 `atan2` známky oba parametry se používá k určení kvadrantu návratovou hodnotu.  
  
|Vstup|Výjimka SEH|Matherr – výjimka|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|žádná|`_DOMAIN`|  
  
## <a name="remarks"></a>Poznámky  
 `atan` Funkce vypočítá Arkus tangens (inverzní funkce tangens) `x`. `atan2` vypočítá Arkus tangens `y` / `x` (Pokud `x` rovná 0, `atan2` vrátí pí/2, pokud `y` kladné, pokud - pí/2 `y` je záporný nebo 0, pokud `y` je 0.)  
  
 `atan` má implementace, která používá Streaming SIMD Extensions 2 (SSE2). Informace a omezení o pomocí implementace SSE2 najdete v tématu [_set_sse2_enable –](../../c-runtime-library/reference/set-sse2-enable.md).  
  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `atan` a `atan2`. V programu C `atan` a `atan2` vždy přijmout a vrátit hodnoty Double.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`atan`, `atan2`, `atanf`, `atan2f`, `atanl`, `atan2l`|\<math.h>|  
  
## <a name="example"></a>Příklad  
  
```  
// crt_atan.c  
// arguments: 5 0.5  
#include <math.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( int ac, char* av[] )   
{  
   double x, y, theta;  
   if( ac != 3 ){  
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );  
      return 1;  
   }  
   x = atof( av[1] );  
   theta = atan( x );  
   printf( "Arctangent of %f: %f\n", x, theta );  
   y = atof( av[2] );  
   theta = atan2( y, x );  
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );   
   return 0;  
}  
```  
  
```Output  
Arctangent of 5.000000: 1.373401  
Arctangent of 0.500000 / 5.000000: 0.099669  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [ACOS, acosf –, acosl –](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [ASIN, asinf –, asinl –](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [Cos, cosf –, cosl –, cosh, coshf –, coshl –](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [_matherr](../../c-runtime-library/reference/matherr.md)   
 [Sin, sinf –, sinl –, sinh, sinhf –, sinhl –](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [Tan, tanf –, tanl –, tanh, tanhf –, tanhl –](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [_CIatan](../../c-runtime-library/ciatan.md)   
 [_CIatan2](../../c-runtime-library/ciatan2.md)