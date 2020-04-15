---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
ms.date: 4/2/2020
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
- _o__nextafter
- _o_nextafter
- _o_nextafterf
- _o_nextafterl
- _o_nexttoward
- _o_nexttowardf
- _o_nexttowardl
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
ms.openlocfilehash: 7b1416147ed000dd3dd9a13bd52e41a474a8e9d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338566"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

Vrátí další reprezentovat hodnotu s plovoucí desetinnou desetinnou hodnotou.

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

*X*<br/>
Hodnota s plovoucí desetinnou tácem, od které chcete začít.

*Y*<br/>
Hodnota s plovoucí desetinnou tágo, ke které se má přibližovat.

## <a name="return-value"></a>Návratová hodnota

Vrátí další reprezentovat hodnotu s plovoucí desetinnou hodnotou návratového typu po *x* ve směru *y*. Pokud *x* a *y* jsou stejné, funkce vrátí *y*, převedena na návratový typ, bez výjimky aktivována. Pokud *x* není rovno *y*a výsledkem je denormální nebo nula, jsou nastaveny **FE_UNDERFLOW** a **FE_INEXACT** stavy výjimek s plovoucí desetinnou desetinnou desetinnou desetinnou a je vrácen správný výsledek. Pokud buď *x* nebo *y* je NAN, pak vrácená hodnota je jedním ze vstupních NANs. Pokud *x* je konečný a výsledek je nekonečný nebo není reprezentovat v typu, je vrácena správně podepsané nekonečno nebo NAN, **FE_OVERFLOW** a **FE_INEXACT** stavy výjimek s plovoucí desetinnou čárkou jsou nastaveny a **errno** je nastavena na **ERANGE**.

## <a name="remarks"></a>Poznámky

Další **po a** **nexttowards** řady funkcí jsou ekvivalentní, s výjimkou typu parametru *y*. Pokud *x* a *y* jsou stejné, vrácená hodnota je *převedena* na návratový typ.

Vzhledem k tomu, že C++ umožňuje přetížení, \<pokud zahrnete cmath> můžete volat přetížení **nextafter** a **nexttowards** tento návrat **float** a **dlouhé** **dvojité** typy. V programu **C, nextafter** a **nexttowards** vždy vrátit **double**.

Funkce **_nextafter** a **_nextafterf** jsou specifické pro společnost Microsoft. Funkce **_nextafterf** je k dispozici pouze při kompilaci pro x64.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Povinná hlavička (C)|Povinné záhlaví (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**, **nextafterf**, **nextafterl**, **_nextafterf**, **nexttowards**, **nexttowardsf**, **nexttowardsl**|\<math.h>|\<math.h> \<nebo cmath>|
|**_nextafter**|\<float.h>|\<float.h> \<nebo cfloat>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
