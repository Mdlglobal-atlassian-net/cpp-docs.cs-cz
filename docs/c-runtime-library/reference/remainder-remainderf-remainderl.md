---
title: remainder, remainderf, remainderl
ms.date: 4/2/2020
api_name:
- remainderl
- remainder
- remainderf
- _o_remainder
- _o_remainderf
- _o_remainderl
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 4b70d3175a125d72ff67710c83899c44dbf72015
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332868"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Vypočítá zbytek podílu dvou hodnot s plovoucí desetinnou desetinnou hodnotou zaokrouhlenou na nejbližší integrální hodnotu.

## <a name="syntax"></a>Syntaxe

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
```

```cpp
float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>Parametry

*X*<br/>
Čitatel.

*Y*<br/>
Jmenovatel.

## <a name="return-value"></a>Návratová hodnota

Zbytek s plovoucí desetinnou tázkem *x* / *y*. Pokud je hodnota *y* 0,0, **zbytek** vrátí tichý NaN. Informace o reprezentaci tiché honosné NaN rodinou **printf** naleznete v [tématu printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Poznámky

Zbývající **remainder** funkce vypočítají *zbytek* s pohyblivou desetinnou třídou *x* / *y* tak, aby *x* = *n* \* *y* + *r*, kde *n*je celé číslo nejbližší v hodnotě *x* / *y* a *n,* i když &#124; *n* - *x* / *y* &#124; = 1/2. Když *r* = 0, *r* má stejné znaménko jako *x*.

Protože C++ umožňuje přetížení, můžete volat přetížení **zbytek,** které trvat a vrátit **float** nebo **dlouhé** **dvojité** hodnoty. V programu C **zbytek** vždy trvá dva **dvojité** argumenty a vrátí **double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Povinná hlavička (C)|Povinné záhlaví (C++)|
|--------------|---------------------|-|
|**zbytek**, **remainderf**, **remainderl**|\<math.h>|\<cmath> \<nebo math.h>|

Informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_remainder.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = remainder(w, x);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
