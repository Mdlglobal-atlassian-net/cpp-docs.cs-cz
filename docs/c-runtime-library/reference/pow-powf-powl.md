---
title: pow, powf, powl
ms.date: 4/2/2020
api_name:
- powl
- pow
- powf
- _o_pow
- _o_powf
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b181959ac05814a673ab11f33e4cfc5a39e3869e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333120"
---
# <a name="pow-powf-powl"></a>pow, powf, powl

Vypočítá *x* zvýšená na mocninu *y*.

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

*X*<br/>
Základní.

*Y*<br/>
Exponent.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu *x*<sup>*y*</sup>. Při přetečení nebo podtečení se netiskne žádná chybová zpráva.

|Hodnoty x a y|Vrácená hodnota pow|
|-----------------------|-------------------------|
|*x* != 0,0 a *y* == 0,0|1|
|*x* == 0,0 a *y* == 0,0|1|
|*x* == 0,0 a *y* < 0|Inf|

## <a name="remarks"></a>Poznámky

**pow** nerozpozná integrální hodnoty s plovoucí desetinnou čárkou větší než 2<sup>64</sup> (například 1.0E100).

**pow** má implementaci, která používá streaming SIMD extensions 2 (SSE2). Informace a omezení týkající se použití implementace SSE2 naleznete [v tématu _set_SSE2_enable](set-sse2-enable.md).

Vzhledem k tomu, že C++ umožňuje přetížení, můžete volat libovolné z různých přetížení **pow**. V programu C **pow** vždy trvá dvě **dvojité** hodnoty a vrátí **dvojitou** hodnotu.

Přetížení `pow(int, int)` již není k dispozici. Pokud použijete toto přetížení, kompilátor může vyzařovat [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md). Chcete-li se tomuto problému vyhnout, přetypujte první parametr na **double**, **float**nebo **long** **double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Povinná hlavička (C)|Povinné záhlaví (C++)|
|-|-|-|
|**pow**, **powf**, **powl**|\<math.h>|\<math.h> \<nebo cmath>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md) <br/>
[sqrt, sqrtf, sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
