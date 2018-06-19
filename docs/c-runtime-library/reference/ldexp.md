---
title: ldexp – ldexpf –, ldexpl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ldexp
- ldexpf
- ldexpl
- _ldexpl
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
- ldexp
- ldexpf
- ldexpl
- _ldexpl
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 012315e11ccf2dbe63e32c6208487f324ef29289
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401413"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp – ldexpf –, ldexpl

Vynásobí celočíselný násobek dvou číslo s plovoucí desetinnou čárkou.

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
Exponent celé číslo.

## <a name="return-value"></a>Návratová hodnota

**Ldexp –** funkce vrátí hodnotu *x* * 2<sup>*exp* </sup> v případě úspěchu. Na přetečení a v závislosti na znaménko *x*, **ldexp –** vrátí **huge_val –**; **errno** nastavena na hodnotu **erange –** .

Další informace o **errno** a možná chyba návratové hodnoty, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **ldexp –** trvají **float** nebo **dlouho** **dvojité** typy. V programu C **ldexp –** má vždy **dvojité** a **int** a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička C|Hlavička C++|
|-------------|--------------|------------------|
|**ldexp –**, **ldexpf –**, **ldexpl**|\<Math.h >|\<cmath – >|

Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
