---
title: sinh, sinhf, sinhl
ms.date: 04/10/2018
api_name:
- sinhl
- sinhf
- sinhl
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
- sinh
- sinhf
- sinhl
helpviewer_keywords:
- sinh function
- sinhl function
- sinhf function
- calculating hyperbolic sines
- trigonometric functions
- sinhf function
- sinhl function
- hyperbolic functions
ms.openlocfilehash: 6ae500cf595707acf9022b1c52232314c36cfe4d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948090"
---
# <a name="sinh-sinhf-sinhl"></a>sinh, sinhf, sinhl

Vypočítá hyperbolický sinus.

## <a name="syntax"></a>Syntaxe

```C
double sinh(double x);
float sinhf(float x);
long double sinhl(long double x);
```

```cpp
float sinh(float x);  // C++ only
long double sinh(long double x);  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Úhel v radiánech.

## <a name="return-value"></a>Návratová hodnota

Funkce **sinh –** vrací hyperbolický sinus *x*. Ve výchozím nastavení platí, že pokud je výsledek příliš velký, **sinh –** nastaví **errno** na **ERANGE** a vrátí ±**HUGE_VAL**.

|Vstup|Výjimka SEH|Výjimka matherr|
|-----------|-------------------|-----------------------|
|QNAN, ZASÁHNOUT|Žádné|_DOMAIN|
|&#124;×&#124; ≥ 7.104760 e + 002|PŘETEČENÍ + NEPŘESNÉ|PLNĚ|

Další informace o návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **sinh –** , která přijímají a vracejí hodnoty **float** nebo **Long** **Double** . V programu v jazyce C **sinh –** vždycky přebírá a vrací **Double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-|-|-|
|**sinh**, **sinhf**, **sinhl**|\<Math. h >|\<cmath > nebo \<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_sinhcosh.c
// This program displays the hyperbolic
// sine and hyperbolic cosine of pi / 2.
// Compile by using: cl /W4 crt_sinhcosh.c

#include <math.h>
#include <stdio.h>

int main( void)
{
   double pi = 3.1415926535;
   double x, y;

   x = pi / 2;
   y = sinh( x );
   printf( "sinh( %f ) = %f\n",x, y );
   y = cosh( x );
   printf( "cosh( %f ) = %f\n",x, y );
}
```

```Output
sinh( 1.570796 ) = 2.301299
cosh( 1.570796 ) = 2.509178
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
