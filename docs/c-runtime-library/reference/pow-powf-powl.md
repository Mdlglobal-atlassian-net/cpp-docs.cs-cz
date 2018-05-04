---
title: Pow –, powf –, powl – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5daf7348198cb6f3ba0186eb4586b2486548f6f5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="pow-powf-powl"></a>pow, powf, powl

Vypočítá *x* umocněné z *y*.

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

Vrátí hodnotu *x*<sup>*y*</sup>. Žádná chybová zpráva je vytištěno na přetečení nebo podtečení.

|Hodnoty x a y|Návratová hodnota pow|
|-----------------------|-------------------------|
|*x* ! = 0,0 a *y* == 0,0|1|
|*x* == 0,0 a *y* == 0,0|1|
|*x* == 0,0 a *y* < 0|INF|

## <a name="remarks"></a>Poznámky

**Pow –** nerozpoznává celočíselné hodnoty s plovoucí desetinnou čárkou větší než 2<sup>64</sup> (například 1.0E100).

**Pow –** má implementace, která používá Streaming SIMD Extensions 2 (SSE2). Informace a omezení o pomocí implementace SSE2 najdete v tématu [_set_sse2_enable –](set-sse2-enable.md).

Protože C++ umožňuje, aby přetížení, můžete volat žádný z různých přetížení **pow**. V programu C **pow** vždy přebírá dva **dvojité** hodnoty a vrátí **dvojité** hodnotu.

`pow(int, int)` Přetížení už není k dispozici. Pokud použijete toto přetížení, může vysílat kompilátor [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md). K tomuto problému nedošlo, přetypovat první parametr **dvojité**, **float**, nebo **dlouho** **dvojité**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-|-|-|
|**Pow –**, **powf –**, **powl –**|\<Math.h >|\<Math.h > nebo \<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md) <br/>
[sqrt, sqrtf, sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
