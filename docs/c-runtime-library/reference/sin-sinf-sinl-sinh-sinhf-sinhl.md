---
title: "Sin, sinf –, sinl –, sinh, sinhf –, sinhl – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sinl
- sinf
- sinhf
- sinh
- sin
- sinhl
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
- _sinl
- sinf
- sinhl
- sinl
- sin
- sinhf
- _sinhl
dev_langs: C++
helpviewer_keywords:
- sinh function
- _sinl function
- _sinhl function
- sinhf function
- sinl function
- calculating sines
- sin function
- trigonometric functions
- sinf function
- sinhl function
- hyperbolic functions
ms.assetid: 737de73e-3590-45f9-8257-dc1c0c489dfc
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f91d8af5b76cb48c884c8eb4466738a544b744b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sin-sinf-sinl-sinh-sinhf-sinhl"></a>sin, sinf, sinl, sinh, sinhf, sinhl
Výpočet sinů a hyperbolický sinů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double sin(  
   double x   
);  
float sin(  
   float x  
);  // C++ only  
long double sin(  
   long double x  
);  // C++ only  
float sinf(  
   float x   
);  
long double sinl(   long double x  
);  
double sinh(  
   double x   
);  
float sinh(  
   float x   
);  // C++ only  
long double sinh(  
   long double x  
);  // C++ only  
float sinhf(  
   float x  
);  
long double sinhl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Úhel v radiánech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `sin` Funkce vrátí sinus `x`. Pokud `x` je větší než nebo rovna hodnotě 263 nebo menší než nebo rovno-263, dojde ke ztrátě násobek ve výsledku.  
  
 `sinh` Funkce Vrátí hyperbolický sinus `x`. Ve výchozím nastavení, pokud je výsledek příliš velký `sinh` nastaví `errno` k `ERANGE` a vrátí rozmezí`HUGE_VAL`.  
  
|Vstup|Výjimka SEH|Matherr – výjimka|  
|-----------|-------------------|-----------------------|  
|ROZMEZÍ QNAN, IND|Žádné|_DOMAIN –|  
|∞ rozmezí (sin, sinf – sinl –.)|NEPLATNÝ|_DOMAIN –|  
|&#124; x &#124; ≥ 7.104760e + 002 (sinh, sinhf – sinhl –.)|PŘETEČENÍ + NEPŘESNÝ|PŘETEČENÍ|  
  
 Další informace o návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `sin` a `sinh` , přijmout a vrátit `float` nebo `long double` hodnoty. V programu C `sin` a `sinh` vždy přijmout a vrátit `double`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`sin`, `sinf`, `sinl`, `sinh`, `sinhf`, `sinhl`|\<Math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_sincos.c  
// This program displays the sine, hyperbolic  
// sine, cosine, and hyperbolic cosine of pi / 2.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = pi / 2;  
   y = sin( x );  
   printf( "sin( %f ) = %f\n", x, y );  
   y = sinh( x );  
   printf( "sinh( %f ) = %f\n",x, y );  
   y = cos( x );  
   printf( "cos( %f ) = %f\n", x, y );  
   y = cosh( x );  
   printf( "cosh( %f ) = %f\n",x, y );  
}  
```  
  
```Output  
sin( 1.570796 ) = 1.000000  
sinh( 1.570796 ) = 2.301299  
cos( 1.570796 ) = 0.000000  
cosh( 1.570796 ) = 2.509178  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [ACOS, acosf –, acosl –](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [ASIN, asinf –, asinl –](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [Atan, atanf –, atanl –, atan2, atan2f –, atan2l –](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [Cos, cosf –, cosl –, cosh, coshf –, coshl –](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [Tan, tanf –, tanl –, tanh, tanhf –, tanhl –](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [_Cisin –](../../c-runtime-library/cisin.md)