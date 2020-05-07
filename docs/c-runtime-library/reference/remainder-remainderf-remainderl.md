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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 6b2a1a94fa39f9e9474f7bc3da3150bf4134d35f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917852"
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

*znak*<br/>
Čitatel.

*požadované*<br/>
Jmenovatel.

## <a name="return-value"></a>Návratová hodnota

Zbytek s plovoucí desetinnou čárkou v *ose x* / *y*. Pokud hodnota *y* je 0,0, **zbytek** vrátí tichou hodnotu NaN. Informace o reprezentace tichého NaN **printf** Family naleznete v tématu [printf, _printf_l, wprintf _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Poznámky

**Zbývající** funkce vypočítávají zbytek s plovoucí desetinnou čárkou *r* z *x* / *y* tak, že *x* = *n* \* *y* + *r*, kde *n*je celé číslo nejbližší hodnotě *x* / *y* a *n*je dokonce vždy, když &#124; *n* - *x* / *y* &#124; = 1/2. Když *r* = 0, *r* má stejné znaménko jako *x*.

Vzhledem k tomu, že jazyk C++ umožňuje přetížení, můžete volat přetížení **zbytku** , která přijímají a vracejí hodnoty **float** nebo **Long** **Double** . V programu v jazyce C **zbytek** vždy přebírá dva **dvojité** argumenty a vrací hodnotu **Double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|--------------|---------------------|-|
|**zbytek**, **remainderf –**, **zbytek**|\<Math. h>|\<cmath> nebo \<Math. h>|

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

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
