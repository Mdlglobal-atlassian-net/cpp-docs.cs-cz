---
title: pow, powf, powl
ms.date: 04/05/2018
api_name:
- powl
- pow
- powf
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
- powl
- pow
- _powl
- powf
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
ms.openlocfilehash: 863d2b76ec131670b10eefc086fa3485bd0a983d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950292"
---
# <a name="pow-powf-powl"></a>pow, powf, powl

Vypočítá *x* umocněnou na mocninu *y*.

## <a name="syntax"></a>Syntaxe

```C
double pow( double x, double y );
float powf( float x, float y );
long double powl( long double x, long double y );
```

```cpp
double pow( double x, int y );  // C++ only
float pow( float x, float y );  // C++ only
float pow( float x, int y );  // C++ only
long double pow( long double x, long double y );  // C++ only
long double pow( long double x, int y );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Základ.

*y*<br/>
Zmocněn.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu *x*<sup>*y*</sup>. V přetečení nebo podtečení není vytištěna žádná chybová zpráva.

|Hodnoty x a y|Návratová hodnota po POW|
|-----------------------|-------------------------|
|*x* ! = 0,0 a *y* = = 0,0|1|
|*x* = = 0,0 a *y* = = 0,0|1|
|*x* = = 0,0 a *y* < 0|SOUBORŮ|

## <a name="remarks"></a>Poznámky

**POW** nerozpoznal celočíselné hodnoty s plovoucí desetinnou čárkou větší než 2<sup>64</sup> (například 1,0 E100).

**POW** má implementaci, která používá streaming SIMD Extensions 2 (SSE2). Informace a omezení týkající se použití implementace SSE2 naleznete v tématu [_set_SSE2_enable](set-sse2-enable.md).

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat kterékoli z různých přetížení po **POW**. V programu v jazyce C, **POW** vždycky přebírá dvě hodnoty **Double** a vrátí hodnotu **Double** .

`pow(int, int)` Přetížení již není k dispozici. Použijete-li toto přetížení, kompilátor může generovat [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md). Chcete-li se tomuto problému vyhnout, přetypujte první parametr na **Double**, **float**nebo **Long** **Double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-|-|-|
|**pow**, **powf**, **powl**|\<Math. h >|\<Math. h > nebo \<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_pow.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.0, y = 3.0, z;

   z = pow( x, y );
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );
}
```

```Output
2.0 to the power of 3.0 is 8.0
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md) <br/>
[sqrt, sqrtf, sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
