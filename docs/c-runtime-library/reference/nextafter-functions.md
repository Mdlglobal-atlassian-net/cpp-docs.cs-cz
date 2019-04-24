---
title: nextafter –, nextafterf –, nextafterl, _nextafter –, _nextafterf, nexttoward, nexttowardf, nexttowardl
ms.date: 04/05/2018
apiname:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
ms.openlocfilehash: 0e0a60dc9f7c068d8c18c10f3c6b819b9e06d3b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156184"
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter –, nextafterf –, nextafterl, _nextafter –, _nextafterf, nexttoward, nexttowardf, nexttowardl

Vrátí následující reprezentovatelnou hodnotu s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
double nextafter( double x, double y );
float nextafterf( float x, float y );
long double nextafterl( long double x, long double y );

double _nextafter( double x, double y );
float _nextafterf( float x, float y ); /* x64 only */

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );
```

```cpp
float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou na spuštění z.

*y*<br/>
Hodnota s plovoucí desetinnou čárkou přejít na.

## <a name="return-value"></a>Návratová hodnota

Vrátí následující reprezentovatelnou hodnotu s plovoucí desetinnou čárkou návratového typu po *x* ve směru *y*. Pokud *x* a *y* rovnají, vrátí funkce hodnotu *y*, převedeno na návratový typ, bez výjimky aktivuje. Pokud *x* není roven *y*, a výsledek je denormal nebo nula, **FE_UNDERFLOW** a **FE_INEXACT** stavy výjimky s plovoucí desetinnou čárkou jsou nastaveny, a vrátí se výsledek správné. Pokud *x* nebo *y* je NAN, vrácená hodnota je jeden vstupní hodnoty NaN. Pokud *x* je však konečný a výsledkem je nekonečné nebo nelze reprezentovat v typu, správně podepsané infinity ani NAN. vrátí se, **FE_OVERFLOW** a **FE_INEXACT** stavy výjimky s plovoucí desetinnou čárkou jsou nastaveny, a **errno** je nastavena na **ERANGE**.

## <a name="remarks"></a>Poznámky

**Nextafter –** a **nexttoward** jsou ekvivalentní, s výjimkou typ parametru funkce rodiny *y*. Pokud *x* a *y* jsou stejné, vrácená hodnota je *y* převést na typ vrácené hodnoty.

Protože jazyk C++ umožňuje přetížení, zadáte-li \<cmath > můžete volat přetížení **nextafter –** a **nexttoward** který vrací **float** a **dlouhé** **double** typy. V programu jazyka C **nextafter –** a **nexttoward** vždy vrátí **double**.

**_Nextafter –** a **_nextafterf** funkce jsou specifické pro Microsoft. **_Nextafterf** funkce je dostupná jenom při kompilaci pro x64.

## <a name="requirements"></a>Požadavky

|Rutina|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**, **nextafterf**, **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf**, **nexttowardl**|\<math.h>|\<Math.h > nebo \<cmath >|
|**_nextafter**|\<float.h >|\<float.h > nebo \<cfloat – >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
