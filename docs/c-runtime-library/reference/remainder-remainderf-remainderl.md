---
title: zbývající, remainderf –, remainderl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f277292f413e09b9c41a87cd82e438e0e1e883a8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Vypočítá zbytek podíl dvou hodnot s plovoucí desetinnou čárkou, zaokrouhlí na nejbližší hodnotu integrálu.

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
Čítači.

*y*<br/>
Jmenovatel.

## <a name="return-value"></a>Návratová hodnota

S plovoucí desetinnou čárkou zbytek *x* / *y*. Pokud hodnota *y* je 0,0, **zbývající** vrátí quiet NaN. Informace o reprezentace quiet NaN pomocí **printf** rodiny, viz [printf _printf_l –, wprintf, _wprintf_l –](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Poznámky

**Zbývající** funkce Výpočet zbytku s plovoucí desetinnou čárkou *r* z *x* / *y* tak, aby *x*   =  *n* * *y* + *r*, kde *n*je v poli hodnota na nejbližší celé číslo *x* / *y* a *n*i je vždy, když &#124; *n*  -  *x* / *y* &#124; = 1/2. Když *r* = 0, *r* má stejné znaménko jako *x*.

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **zbývající** , přijmout a vrátit **float** nebo **dlouho** **dvojité** hodnoty. V programu C **zbývající** vždy přebírá dva **dvojité** argumentů a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|--------------|---------------------|-|
|**zbývající**, **remainderf –**, **remainderl**|\<Math.h >|\<cmath – > nebo \<math.h >|

Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
