---
title: nextafter –, nextafterf –, nextafterl, _nextafter –, _nextafterf, nexttoward, nexttowardf, nexttowardl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c68d039ff1318ea082d409078a55c8d337a48de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter –, nextafterf –, nextafterl, _nextafter –, _nextafterf, nexttoward, nexttowardf, nexttowardl

Vrátí hodnotu dalšího reprezentovat s plovoucí desetinnou čárkou.

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
Hodnota s plovoucí desetinnou čárkou spuštění z.

*y*<br/>
Hodnota s plovoucí desetinnou čárkou přejdete směrem.

## <a name="return-value"></a>Návratová hodnota

Vrací další reprezentovat s plovoucí desetinnou čárkou hodnotu návratového typu po *x* ve směru *y*. Pokud *x* a *y* jsou stejné, funkce vrátí hodnotu *y*, převést na návratový typ se žádná výjimka pro aktivaci. Pokud *x* se nerovná *y*, a výsledkem je, denormal nebo nula, **FE_UNDERFLOW** a **FE_INEXACT** stavy výjimek plovoucí desetinné čárky jsou nastaveny, a je vrácen správný výsledek. Pokud má jedna *x* nebo *y* je NAN, pak návratová hodnota je jedním z vstupní hodnoty NaN. Pokud *x* je omezený a výsledek je nekonečné nebo nelze reprezentovat typ, správně podepsané infinity ani NAN se vrátí, **FE_OVERFLOW** a **FE_INEXACT** jsou nastavené stavy výjimek plovoucí desetinné čárky, a **errno** je nastaven na **erange –**.

## <a name="remarks"></a>Poznámky

**Nextafter –** a **nexttoward** jsou ekvivalentní s výjimkou typu parametru funkce rodiny *y*. Pokud *x* a *y* jsou stejné, je vrácena hodnota *y* převést na návratový typ.

Protože C++ umožňuje přetížení, pokud zahrnete \<cmath – > můžete volat přetížení **nextafter –** a **nexttoward** který vrací **float** a **dlouho** **dvojité** typy. V programu C **nextafter –** a **nexttoward** vždy vrátí **dvojité**.

**_Nextafter –** a **_nextafterf** funkce se konkrétní společnosti Microsoft. **_Nextafterf** funkce je k dispozici pouze při kompilaci pro x64.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter –**, **nextafterf –**, **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf** , **nexttowardl**|\<Math.h >|\<Math.h > nebo \<cmath – >|
|**_nextafter**|\<float.h – >|\<float.h – > nebo \<cfloat – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
