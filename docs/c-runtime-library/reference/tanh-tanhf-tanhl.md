---
title: TANH, tanhf –, tanhl
ms.date: 04/10/2018
apiname:
- tanh
- tanhf
- tanhl
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
- tanh
- tanhf
- tanhl
- _tanhl
helpviewer_keywords:
- tanhl function
- _tanhl function
- tanh function
- tanhf function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: 3b9c7269d3c945301106098fc944383bbc364e5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432383"
---
# <a name="tanh-tanhf-tanhl"></a>TANH, tanhf –, tanhl

Vypočte hyperbolický tangens.

## <a name="syntax"></a>Syntaxe

```C
double tanh( double x );
float tanhf( float x );
long double tanhl( long double x );
```

```cpp
float tanh( float x );  // C++ only
long double tanh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Úhel v radiánech.

## <a name="return-value"></a>Návratová hodnota

**Tanh** funkce vrací hyperbolický tangens *x*. Není vrácena žádná chyba.

|Vstup|Výjimka SEH|**Matherr** výjimky|
|-----------|-------------------|-------------------------|
|ROZMEZÍ QNAN, AJÍT|žádná|_DOMÉNA|

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **tanh** , která používají a vrací **float** nebo **dlouhé** **double** hodnoty. V programu jazyka C **tanh** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadované záhlaví (C)|Požadované záhlaví (C)|
|-------------|---------------------|-|
|**TANH**, **tanhf –**, **tanhl**|\<Math.h >|\<cmath > nebo \<math.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_tanh.c
// This program displays the tangent of pi / 4
// and the hyperbolic tangent of the result.
// Compile by using: cl crt_tanh.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = tan( pi / 4 );
   y = tanh( x );
   printf( "tan( %f ) = %f\n", pi/4, x );
   printf( "tanh( %f ) = %f\n", x, y );
}
```

```Output
tan( 0.785398 ) = 1.000000
tanh( 1.000000 ) = 0.761594
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
