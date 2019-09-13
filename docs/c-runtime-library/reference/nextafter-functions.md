---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
ms.date: 04/05/2018
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
ms.openlocfilehash: c56c9f8032c9af2ed4404428abe3b9ee26b4b603
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951358"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

Vrátí další reprezentovatelné číslo s plovoucí desetinnou čárkou.

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
Hodnota s plovoucí desetinnou čárkou, ze které se má začít.

*y*<br/>
Hodnota s plovoucí desetinnou čárkou, která má jít směrem k.

## <a name="return-value"></a>Návratová hodnota

Vrátí další reprezentovatelné číslo s plovoucí desetinnou čárkou pro návratový typ po *x* ve směru *y*. Pokud jsou *x* a *y* stejné, funkce vrátí *y*, převedeno na návratový typ bez vyvolání výjimky. Pokud *x* není rovno *y*a výsledkem je nenormální nebo nula, stavy výjimek s plovoucí desetinnou čárkou **FE_UNDERFLOW** a **FE_INEXACT** jsou nastaveny a je vrácen správný výsledek. Pokud je hodnota *x* nebo *y* NaN, pak je návratovou hodnotou jedna ze vstupních hodnoty NaN. Pokud je hodnota *x* konečná a výsledek je nekonečný nebo se nedá reprezentovat v typu, vrátí se správně podepsané nekonečno nebo NaN, **FE_OVERFLOW** a **FE_INEXACT** stavy výjimky s plovoucí desetinnou čárkou a **errno** je nastaveno na **ERANGE** .

## <a name="remarks"></a>Poznámky

Rodiny funkcí **nextafter –** a **nexttoward** jsou ekvivalentní, s výjimkou typu parametru *y*. Pokud jsou hodnoty *x* a *y* stejné, vrácená hodnota je *y* převedena na návratový typ.

Protože C++ umožňuje \<přetížení, pokud zahrnete cmath > můžete volat přetížení **nextafter –** a **nexttoward** , které vracejí **float** a **Long** **Double** Types. V programu v jazyce C **nextafter –** a **nexttoward** vždycky vrací hodnotu **Double**.

Funkce **_nextafter** a **_nextafterf** jsou specifické pro společnost Microsoft. Funkce **_nextafterf** je k dispozici pouze při kompilaci pro x64.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter –** , **nextafterf –** , **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf**, **nexttowardl**|\<Math. h >|\<Math. h > nebo \<cmath >|
|**_nextafter**|\<float. h >|\<float. h > nebo \<cfloat >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
