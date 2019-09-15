---
title: atanh, atanhf, atanhl
ms.date: 04/05/2018
api_name:
- atanhl
- atanhf
- atanh
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- atanhl
- atanhf
- atanh
helpviewer_keywords:
- atanhf function
- atanhl function
- atanh funciton
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
ms.openlocfilehash: 539d015d5691f62f990faf650ab738f60066a2a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939586"
---
# <a name="atanh-atanhf-atanhl"></a>atanh, atanhf, atanhl

Vypočítá inverzní hyperbolický tangens.

## <a name="syntax"></a>Syntaxe

```C
double atanh( double x );
float atanhf( float x );
long double atanhl( long double x );
```

```cpp
float atanh( float x );  // C++ only
long double atanh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Funkce **atanh –** vrátí inverzní arkustangens tangens (oblouk hyperbolický tangens) *x*. Pokud je *x* větší než 1 nebo menší než-1, **errno** je nastaveno na **EDOM** a výsledek je tiché NaN. Pokud je *x* rovno 1 nebo-1, vrátí se kladné nebo záporné nekonečno, v uvedeném pořadí a **errno** je nastavena na **ERANGE**.

|Vstup|Výjimka SEH|**Matherr** Jímka|
|-----------|-------------------|-------------------------|
|QNAN, ZASÁHNOUT|žádná|žádná|
|*X* ≥ 1; *x* ≤ -1|žádná|žádná|

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **atanh –** , která přijímají a vracejí hodnoty **float** nebo **Long** **Double** . V programu v jazyce C **atanh –** vždycky přebírá a vrací **Double**.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**atanh –** , **atanhf –** , **atanhl**|\<Math. h >|\<cmath > nebo \<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
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

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
