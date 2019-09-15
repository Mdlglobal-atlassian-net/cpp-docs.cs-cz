---
title: ldexp –, ldexpf –, ldexpl
ms.date: 04/05/2018
api_name:
- ldexp
- ldexpf
- ldexpl
- _ldexpl
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
- ldexp
- ldexpf
- ldexpl
- _ldexpl
helpviewer_keywords:
- calculating real numbers
- computing real numbers
- mantissas, floating-point variables
- ldexp function
- ldexpf function
- ldexpl function
- exponent, floating-point numbers
- floating-point functions, mantissa and exponent
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
ms.openlocfilehash: 7fabd00c7ddc5c430c158089b7e5769158b46328
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953507"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp –, ldexpf –, ldexpl

Vynásobí číslo s plovoucí desetinnou čárkou integrálním výkonem dvou.

## <a name="syntax"></a>Syntaxe

```C
double ldexp(
   double x,
   int exp
);
float ldexp(
   float x,
   int exp
);  // C++ only
long double ldexp(
   long double x,
   int exp
);  // C++ only
float ldexpf(
   float x,
   int exp
);
long double ldexpl(
   long double x,
   int exp
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

*exp*<br/>
Celočíselný exponent.

## <a name="return-value"></a>Návratová hodnota

Funkce **ldexp –** vrací hodnotu *x* \* 2<sup>*exp*</sup> , pokud je úspěšná. Při přetečení a v závislosti na znaménku *x* **ldexp –** vrátí +/- **HUGE_VAL**; hodnota **errno** je nastavená na **ERANGE**.

Další informace o **errno** a možných návratových hodnotách chyb naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **ldexp –** , která přebírají **float** nebo **Long** **Double** Types. V programu v jazyce C **ldexp –** vždy přebírá **Double** a **int** a vrací hodnotu **Double**.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička jazyka C|C++hlaviček|
|-------------|--------------|------------------|
|**ldexp –** , **ldexpf –** , **ldexpl**|\<Math. h >|\<cmath >|

Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_ldexp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 4.0, y;
   int p = 3;

   y = ldexp( x, p );
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );
}
```

## <a name="output"></a>Výstup

```Output
4.0 times two to the power of 3 is 32.0
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
