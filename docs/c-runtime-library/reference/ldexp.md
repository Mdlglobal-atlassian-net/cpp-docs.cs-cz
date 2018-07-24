---
title: ldexp – ldexpf –, ldexpl | Dokumentace Microsoftu
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
ms.openlocfilehash: 8ead91ce542ce547f9453f52455dc76d61045b87
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208412"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp – ldexpf –, ldexpl

Vynásobí číslo s plovoucí desetinnou čárkou integrální mocninou čísla 2.

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

**Ldexp –** vrátí funkce hodnotu *x* \* 2<sup>*exp* </sup> v případě úspěšného ověření. Při přetečení a v závislosti na znaménko *x*, **ldexp –** vrátí **HUGE_VAL**; **errno** nastavena na hodnotu **ERANGE** .

Další informace o **errno** a možnou chybu návratové hodnoty, najdete v článku [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **ldexp –** trvají **float** nebo **dlouhé** **double** typy. V programu jazyka C **ldexp –** vždy přijímá **double** a **int** a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Rutina|Záhlaví C|Hlaviček jazyka C++|
|-------------|--------------|------------------|
|**ldexp –**, **ldexpf –**, **ldexpl**|\<Math.h >|\<cmath >|

Informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
