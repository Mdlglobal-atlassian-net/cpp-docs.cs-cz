---
title: remainder, remainderf, remainderl
ms.date: 04/05/2018
apiname:
- remainderl
- remainder
- remainderf
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 9a9abe82e69122ca87f44e293e1da725c97045d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572741"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Vypočítá zbytek z podílu dvou hodnot s plovoucí desetinnou čárkou, zaokrouhlí na nejbližší celočíselnou hodnotu.

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

*x*<br/>
Čítač.

*y*<br/>
Jmenovatel.

## <a name="return-value"></a>Návratová hodnota

Zbytek s plovoucí desetinnou čárkou z *x* / *y*. Pokud hodnota *y* je 0,0, **zbývající** vrátí tichý NaN. Informace o reprezentaci tichého NaN **printf** řady, viz [printf _printf_l –, wprintf _wprintf_l –](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Poznámky

**Zbývající** funkce vypočítá zbytek s plovoucí desetinnou čárkou *r* z *x* / *y* tak, aby *x*   =  *n* \* *y* + *r*, kde *n*je v hodnotě na nejbližší celé číslo *x* / *y* a *n*sudé pokaždé, když &#124; *n*  -  *x* / *y* &#124; = 1/2. Když *r* = 0, *r* má stejné znaménko jako *x*.

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **zbývající** , která používají a vrací **float** nebo **dlouhé** **double** hodnoty. V programu jazyka C **zbývající** vždy má dva **double** argumenty a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|--------------|---------------------|-|
|**zbývající**, **remainderf –**, **remainderl**|\<Math.h >|\<cmath > nebo \<math.h >|

Informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
