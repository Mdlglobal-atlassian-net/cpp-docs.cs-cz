---
title: pow, powf, powl
ms.date: 04/05/2018
apiname:
- powl
- pow
- powf
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
ms.openlocfilehash: edf6116413caba52f9311f03bdfcc1d87e68a011
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452004"
---
# <a name="pow-powf-powl"></a>pow, powf, powl

Vypočítá *x* umocněné na sílu *y*.

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
Exponent.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu *x*<sup>*y*</sup>. Žádná chybová zpráva vytištěna na přetečení nebo podtečení.

|Hodnoty x a y|Návratová hodnota pow|
|-----------------------|-------------------------|
|*x* ! = 0,0 a *y* == 0,0|1|
|*x* == 0,0 a *y* == 0,0|1|
|*x* == 0,0 a *y* < 0|INF|

## <a name="remarks"></a>Poznámky

**Pow** nerozpozná integrální hodnoty s plovoucí desetinnou čárkou větší než 2<sup>64</sup> (například 1.0E100).

**Pow** má implementace, která používá Streaming SIMD Extensions 2 (SSE2). Informace a omezení týkající se použití implementace SSE2, naleznete v tématu [_set_sse2_enable –](set-sse2-enable.md).

Protože jazyk C++ umožňuje přetížení, můžete volat některý z různých přetížení **pow**. V programu jazyka C **pow** vždy má dva **double** hodnoty a vrátí **double** hodnotu.

`pow(int, int)` Přetížení již není k dispozici. Pokud použijete toto přetížení, kompilátor může vygenerovat [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md). K tomuto problému vyhnout, přetypování první parametr **double**, **float**, nebo **dlouhé** **double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|-|-|-|
|**Pow**, **powf –**, **powl –**|\<Math.h >|\<Math.h > nebo \<cmath >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
