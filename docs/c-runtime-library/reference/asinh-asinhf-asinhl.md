---
title: "asinh – asinhf –, asinhl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- asinh
- asinhf
- asinhl
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
- asinhf
- asinhl
- asinh
dev_langs: C++
helpviewer_keywords:
- asinh function
- asinhl function
- asinhf function
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20e03e80517726689c7d3369e0afc4de30bcf230
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="asinh-asinhf-asinhl"></a>asinh, asinhf, asinhl
Vypočítá inverzní hyperbolický sinus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double asinh(  
   double x   
);  
float asinh(  
   float x   
);  // C++ only  
long double asinh(  
   long double x  
);  // C++ only  
float asinhf(  
   float x   
);  
long double asinhl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Hodnota s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 `asinh` Funkce vrátí hyberbolic inverzní sinus (oblouk hyperbolický sinus) `x`. Tato funkce je platný doménou, s plovoucí desetinnou čárkou. Pokud `x` quiet NaN, neomezené, nebo infinity, je vrácena stejnou hodnotu.  
  
|Vstup|Výjimka SEH|`_matherr`Výjimka|  
|-----------|-------------------|--------------------------|  
|INF QNAN, IND PŘESNOSTÍ|žádná|žádná|  
  
## <a name="remarks"></a>Poznámky  
 Pokud používáte C++, můžete volat přetížení `asinh` , přijmout a vrátit `float` nebo `long double` hodnoty. V programu C `asinh` vždy provede a vrátí `double`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`asinh`, `asinhf`, `asinhl`|\<Math.h >|\<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_asinh.c  
// Compile by using: cl /W4 crt_asinh.c  
// This program displays the hyperbolic sine of pi / 4  
// and the arc hyperbolic sine of the result.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = sinh( pi / 4 );  
   y = asinh( x );  
   printf( "sinh( %f ) = %f\n", pi/4, x );  
   printf( "asinh( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
sinh( 0.785398 ) = 0.868671  
asinh( 0.868671 ) = 0.785398  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [Cos, cosf –, cosl –, cosh, coshf –, coshl –](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [acosh – acoshf –, acoshl](../../c-runtime-library/reference/acosh-acoshf-acoshl.md)   
 [Sin, sinf –, sinl –, sinh, sinhf –, sinhl –](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [Tan, tanf –, tanl –, tanh, tanhf –, tanhl –](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [atanh – atanhf –, atanhl –](../../c-runtime-library/reference/atanh-atanhf-atanhl.md)   
 [_Citan –](../../c-runtime-library/citan.md)