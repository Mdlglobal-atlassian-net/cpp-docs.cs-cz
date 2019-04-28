---
title: asinh, asinhf, asinhl
ms.date: 04/05/2018
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
helpviewer_keywords:
- asinh function
- asinhl function
- asinhf function
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
ms.openlocfilehash: f6100268b77178487b7a7aa1cc3f10ac3ea7e9dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341779"
---
# <a name="asinh-asinhf-asinhl"></a>asinh, asinhf, asinhl

Vypočítá inverzní hyperbolický sinus.

## <a name="syntax"></a>Syntaxe

```C
double asinh( double x );
float asinhf( float x );
long double asinhl( long double x );
```

```cpp
float asinh( float x );  // C++ only
long double asinh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

**Asinh –** funkce vrátí hyberbolic inverzní sinus (hyperbolický Arkus sinus) *x*. Tato funkce je platný v doméně s plovoucí desetinnou čárkou. Pokud *x* je tichý NaN, nekonečno, nebo nekonečno, je vrácena stejnou hodnotu.

|Vstup|Výjimka SEH|**_matherr** Exception|
|-----------|-------------------|--------------------------|
|ROZMEZÍ QNAN, AJÍT INF|žádná|žádná|

## <a name="remarks"></a>Poznámky

Při použití jazyka C++, můžete volat přetížení **asinh –** , která používají a vrací **float** nebo **dlouhé** **double** hodnoty. V programu jazyka C **asinh –** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička C|Požadované hlaviček jazyka C++|
|--------------|--------------|------------------|
|**asinh**, **asinhf**, **asinhl**|\<math.h>|\<cmath > nebo \<math.h <|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
