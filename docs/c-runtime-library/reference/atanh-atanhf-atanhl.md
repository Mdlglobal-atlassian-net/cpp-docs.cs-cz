---
title: "atanh – atanhf –, atanhl – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- atanhl
- atanhf
- atanh
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
- atanhl
- atanhf
- atanh
dev_langs: C++
helpviewer_keywords:
- atanhf function
- atanhl function
- atanh funciton
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7e21b07685943559bace8b8e2b0fbdebdb3a870c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atanh-atanhf-atanhl"></a>atanh, atanhf, atanhl
Vypočítá inverzní hyperbolický tangens.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double atanh(  
   double x   
);  
float atanh(  
   float x   
);  // C++ only  
long double atanh(  
   long double x  
);  // C++ only  
float atanhf(  
   float x   
);  
long double atanhl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Hodnota s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 `atanh` Funkce vrátí hyberbolic inverzní tangens (oblouk hyperbolický tangens) `x`. Pokud `x` je větší než 1 a menší než -1, `errno` je nastaven na `EDOM` a výsledkem je quiet NaN. Pokud `x` se rovná 1 nebo -1, kladné a záporné infinity se vrátí, v uvedeném pořadí, a `errno` je nastaven na `ERANGE`.  
  
|Vstup|Výjimka SEH|`Matherr`Výjimka|  
|-----------|-------------------|-------------------------|  
|ROZMEZÍ QNAN, IND|žádná|žádná|  
|`X` ≥ 1; `x` ≤ -1|žádná|žádná|  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `atanh` , přijmout a vrátit `float` nebo `long double` hodnoty. V programu C `atanh` vždy provede a vrátí `double`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`atanh`, `atanhf`, `atanhl`|\<Math.h >|\<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_atanh.c  
// This program displays the hyperbolic tangent of pi / 4  
// and the arc hyperbolic tangent of the result.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = tanh( pi / 4 );  
   y = atanh( x );  
   printf( "tanh( %f ) = %f\n", pi/4, x );  
   printf( "atanh( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
tanh( 0.785398 ) = 0.655794  
atanh( 0.655794 ) = 0.785398  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [ACOS, acosf –, acosl –](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [ASIN, asinf –, asinl –](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [Atan, atanf –, atanl –, atan2, atan2f –, atan2l –](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [Cos, cosf –, cosl –, cosh, coshf –, coshl –](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [Sin, sinf –, sinl –, sinh, sinhf –, sinhl –](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [Tan, tanf –, tanl –, tanh, tanhf –, tanhl –](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [_Citan –](../../c-runtime-library/citan.md)