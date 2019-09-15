---
title: remainder, remainderf, remainderl
ms.date: 04/05/2018
api_name:
- remainderl
- remainder
- remainderf
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 851f022325bb617cb2b0ae9a331b680b9d9fd303
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949414"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Vypočítá zbytek podílu dvou hodnot s plovoucí desetinnou čárkou zaokrouhlený na nejbližší celočíselnou hodnotu.

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
Čitatel.

*y*<br/>
Jmenovatel.

## <a name="return-value"></a>Návratová hodnota

Zbytek s plovoucí desetinnou čárkou v *ose x* / *y*. Pokud hodnota *y* je 0,0, **zbytek** vrátí tichou hodnotu NaN. Informace o reprezentace tichého NaN **printf** Family naleznete v tématu [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Poznámky

**Zbývající** funkce vypočítávají zbytek s plovoucí desetinnou čárkou *r* z *x* / *y* tak, aby *x* = *n* \* *y* + *r*, kde *n* je celé číslo nejbližší hodnoty na *ose x* / a *n*i &#124; v*případě, že* je *n* - *×* / *y* &#124; = 1/2. Když *r* = 0, *r* má stejné znaménko jako *x*.

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **zbytku** , která přijímají a vracejí hodnoty **float** nebo **Long** **Double** . V programu v jazyce C **zbytek** vždy přebírá dva **dvojité** argumenty a vrací hodnotu **Double**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|--------------|---------------------|-|
|**zbytek**, **remainderf –** , **zbytek**|\<Math. h >|\<cmath > nebo \<Math. h >|

Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
