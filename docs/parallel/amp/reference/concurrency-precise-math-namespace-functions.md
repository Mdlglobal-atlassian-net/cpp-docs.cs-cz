---
title: Funkce oboru názvů Concurrency::precise_math
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::precise_math::acos
- amp_math/Concurrency::precise_math::acosh
- amp_math/Concurrency::precise_math::acoshf
- amp_math/Concurrency::precise_math::asinf
- amp_math/Concurrency::precise_math::asinh
- amp_math/Concurrency::precise_math::atan
- amp_math/Concurrency::precise_math::atan2
- amp_math/Concurrency::precise_math::atanf
- amp_math/Concurrency::precise_math::atanh
- amp_math/Concurrency::precise_math::cbrt
- amp_math/Concurrency::precise_math::cbrtf
- amp_math/Concurrency::precise_math::ceilf
- amp_math/Concurrency::precise_math::copysign
- amp_math/Concurrency::precise_math::cos
- amp_math/Concurrency::precise_math::cosf
- amp_math/Concurrency::precise_math::coshf
- amp_math/Concurrency::precise_math::cospi
- amp_math/Concurrency::precise_math::erf
- amp_math/Concurrency::precise_math::erfc
- amp_math/Concurrency::precise_math::erfcinv
- amp_math/Concurrency::precise_math::erfcinvf
- amp_math/Concurrency::precise_math::erfinv
- amp_math/Concurrency::precise_math::erfinvf
- amp_math/Concurrency::precise_math::exp10
- amp_math/Concurrency::precise_math::exp10f
- amp_math/Concurrency::precise_math::exp2f
- amp_math/Concurrency::precise_math::expf
- amp_math/Concurrency::precise_math::expm1f
- amp_math/Concurrency::precise_math::fabs
- amp_math/Concurrency::precise_math::floor
- amp_math/Concurrency::precise_math::fdim
- amp_math/Concurrency::precise_math::floorf
- amp_math/Concurrency::precise_math::fmaf
- amp_math/Concurrency::precise_math::fmaxf
- amp_math/Concurrency::precise_math::fmin
- amp_math/Concurrency::precise_math::fmod
- amp_math/Concurrency::precise_math::fmodf
- amp_math/Concurrency::precise_math::frexp
- amp_math/Concurrency::precise_math::frexpf
- amp_math/Concurrency::precise_math::hypotf
- amp_math/Concurrency::precise_math::ilogb
- amp_math/Concurrency::precise_math::isfinite
- amp_math/Concurrency::precise_math::isinf
- amp_math/Concurrency::precise_math::isnormal
- amp_math/Concurrency::precise_math::ldexp
- amp_math/Concurrency::precise_math::lgamma
- amp_math/Concurrency::precise_math::lgammaf
- amp_math/Concurrency::precise_math::log10
- amp_math/Concurrency::precise_math::log10f
- amp_math/Concurrency::precise_math::log1pf
- amp_math/Concurrency::precise_math::log2
- amp_math/Concurrency::precise_math::logb
- amp_math/Concurrency::precise_math::logbf
- amp_math/Concurrency::precise_math::modf
- amp_math/Concurrency::precise_math::modff
- amp_math/Concurrency::precise_math::nanf
- amp_math/Concurrency::precise_math::nearbyint
- amp_math/Concurrency::precise_math::nextafter
- amp_math/Concurrency::precise_math::nextafterf
- amp_math/Concurrency::precise_math::phif
- amp_math/Concurrency::precise_math::pow
- amp_math/Concurrency::precise_math::probit
- amp_math/Concurrency::precise_math::probitf
- amp_math/Concurrency::precise_math::rcbrtf
- amp_math/Concurrency::precise_math::remainder
- amp_math/Concurrency::precise_math::remquo
- amp_math/Concurrency::precise_math::remquof
- amp_math/Concurrency::precise_math::roundf
- amp_math/Concurrency::precise_math::rsqrt
- amp_math/Concurrency::precise_math::scalb
- amp_math/Concurrency::precise_math::scalbf
- amp_math/Concurrency::precise_math::scalbnf
- amp_math/Concurrency::precise_math::signbit
- amp_math/Concurrency::precise_math::sin
- amp_math/Concurrency::precise_math::sincos
- amp_math/Concurrency::precise_math::sinf
- amp_math/Concurrency::precise_math::sinh
- amp_math/Concurrency::precise_math::sinpi
- amp_math/Concurrency::precise_math::sinpif
- amp_math/Concurrency::precise_math::sqrtf
- amp_math/Concurrency::precise_math::tan
- amp_math/Concurrency::precise_math::tanh
- amp_math/Concurrency::precise_math::tanhf
- amp_math/Concurrency::precise_math::tanpif
- amp_math/Concurrency::precise_math::tgamma
- amp_math/Concurrency::precise_math::trunc
- amp_math/Concurrency::precise_math::truncf
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
ms.openlocfilehash: 53ebaf8d9cc1bca53b1fe51464668d6df8e08424
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419243"
---
# <a name="concurrencyprecise_math-namespace-functions"></a>Funkce oboru názvů Concurrency::precise_math

||||
|-|-|-|
|[acos](#acos)|[acosf –](#acosf)|[acosh –](#acosh)|
|[acoshf –](#acoshf)|[ASIN](#asin)|[asinf –](#asinf)|
|[asinh –](#asinh)|[asinhf –](#asinhf)|[atan](#atan)|
|[funkce](#atan2)|[atan2f –](#atan2f)|[atanf –](#atanf)|
|[atanh –](#atanh)|[atanhf –](#atanhf)|[cbrt –](#cbrt)|
|[cbrtf –](#cbrtf)|[ceil –](#ceil)|[ceilf –](#ceilf)|
|[copysign –](#copysign)|[copysignf –](#copysignf)|[Cos](#cos)|
|[cosf –](#cosf)|[cosh –](#cosh)|[coshf –](#coshf)|
|[cospi –](#cospi)|[cospif –](#cospif)|[ERF](#erf)|
|[ERFC –](#erfc)|[erfcf –](#erfcf)|[erfcinv –](#erfcinv)|
|[erfcinvf –](#erfcinvf)|[erff –](#erff)|[erfinv –](#erfinv)|
|[erfinvf –](#erfinvf)|[oček](#exp)|[exp10 –](#exp10)|
|[exp10f –](#exp10f)|[exp2 –](#exp2)|[exp2f –](#exp2f)|
|[expf –](#expf)|[expm1 –](#expm1)|[expm1f –](#expm1f)|
|[fabs –](#fabs)|[fabsf –](#fabsf)|[řízení](#floor)|
|[fdim –](#fdim)|[fdimf –](#fdimf)||
|[floorf –](#floorf)|[FMA](#fma)|[fmaf –](#fmaf)|
[Fmax –](#fmax)|[fmaxf –](#fmaxf)||
|[fmin –](#fmin)|[fminf –](#fminf)|[FMOD –](#fmod)|
|[fmodf –](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf –](#frexpf)|[hypot –](#hypot)|[hypotf –](#hypotf)|
|[ilogb –](#ilogb)|[ilogbf –](#ilogbf)|[isfinite –](#isfinite)|
|[isinf](#isinf)|[IsNaN](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[ldexpf –](#ldexpf)|[lgamma –](#lgamma)|
|[lgammaf –](#lgammaf)|[protokolu](#log)|[log10 –](#log10)|
|[log10f –](#log10f)|[log1p –](#log1p)|[log1pf –](#log1pf)|
|[log2 –](#log2)|[log2f –](#log2f)|[logb –](#logb)|
|[logbf –](#logbf)|[logf –](#logf)|[modf –](#modf)|
|[modff –](#modff)|[pak](#nan)|[nanf –](#nanf)|
|[nearbyint –](#nearbyint)|[nearbyintf –](#nearbyintf)|[nextafter –](#nextafter)|
|[nextafterf –](#nextafterf)|[fí](#phi)|[phif](#phif)|
|[log](#pow)|[powf –](#powf)|[probit](#probit)|
|[probitf](#probitf)|[rcbrt –](#rcbrt)|[rcbrtf –](#rcbrtf)|
|[Hledáte](#remainder)|[remainderf –](#remainderf)|[remquo –](#remquo)|
|[remquof –](#remquof)|[zpoždění](#round)|[roundf –](#roundf)|
|[rsqrt –](#rsqrt)|[rsqrtf –](#rsqrtf)|[scalb –](#scalb)|
|[scalbf –](#scalbf)|[scalbn –](#scalbn)|[scalbnf –](#scalbnf)|
|[signbit](#signbit)|[signbitf –](#signbitf)|[tlačítek](#sin)|
|[sincos –](#sincos)|[sincosf –](#sincosf)|[sinf –](#sinf)|
|[sinh –](#sinh)|[sinhf –](#sinhf)|[sinpi –](#sinpi)|
|[sinpif –](#sinpif)|[SQRT](#sqrt)|[sqrtf –](#sqrtf)|
|[nádrž](#tan)|[tanf –](#tanf)|[tanh –](#tanh)|
|[tanhf –](#tanhf)|[tanpi –](#tanpi)|[tanpif –](#tanpif)|
|[tgamma –](#tgamma)|[tgammaf –](#tgammaf)|[TRUNC –](#trunc)|
|[truncf –](#truncf)|

## <a name="acos"></a>acos

Vypočítá Arkus kosinus argumentu.

```cpp
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus kosinus argumentu.

## <a name="acosf"></a>acosf –

Vypočítá Arkus kosinus argumentu.

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus kosinus argumentu.

## <a name="acosh"></a>acosh –

Vypočítá inverzní hyperbolický kosinus argumentu.

```cpp
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací inverzní hodnotu hyperbolický kosinus argumentu.

## <a name="acoshf"></a>acoshf –

Vypočítá inverzní hyperbolický kosinus argumentu.

```cpp
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací inverzní hodnotu hyperbolický kosinus argumentu.

## <a name="asin"></a>ASIN

Vypočítá Arkus sinus argumentu.

```cpp
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus sinus argumentu.

## <a name="asinf"></a>asinf –

Vypočítá Arkus sinus argumentu.

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus sinus argumentu.

## <a name="asinh"></a>asinh –

Vypočítá inverzní hyperbolický sinus argumentu.

```cpp
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní hodnotu hyperbolický sinus argumentu.

## <a name="asinhf"></a>asinhf –

Vypočítá inverzní hyperbolický sinus argumentu.

```cpp
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní hodnotu hyperbolický sinus argumentu.

## <a name="atan"></a>atan

Vypočítá arkustangens argumentu

```cpp
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arkustangens argumentu.

## <a name="atan2"></a>funkce

Vypočítá arkustangens _Y/_X

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);

inline double atan2(
    double _Y,
    double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus tangens _Y/_X.

## <a name="atan2f"></a>atan2f –

Vypočítá arkustangens _Y/_X

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus tangens _Y/_X.

## <a name="atanf"></a>atanf –

Vypočítá arkustangens argumentu

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arkustangens argumentu.

## <a name="atanh"></a>atanh –

Vypočítá inverzní hyperbolický tangens argumentu.

```cpp
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací inverzní hodnotu hyperbolický tangens argumentu.

## <a name="atanhf"></a>atanhf –

Vypočítá inverzní hyperbolický tangens argumentu.

```cpp
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací inverzní hodnotu hyperbolický tangens argumentu.

## <a name="cbrt"></a>cbrt –

Vypočítá kořen reálné datové krychle argumentu.

```cpp
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kořen reálné datové krychle argumentu.

## <a name="cbrtf"></a>cbrtf –

Vypočítá kořen reálné datové krychle argumentu.

```cpp
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kořen reálné datové krychle argumentu.

## <a name="ceil"></a>ceil –

Vypočítá strop argumentu.

```cpp
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí strop argumentu.

## <a name="ceilf"></a>ceilf –

Vypočítá strop argumentu.

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí strop argumentu.

## <a name="copysign"></a>copysign –

Vytvoří hodnotu s velikostí _X a znaménkem _Y

```cpp
inline float copysign(
    float _X,
    float _Y) restrict(amp);

inline double copysign(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu s velikostí _X a znaménkem _Y

## <a name="copysignf"></a>copysignf –

Vytvoří hodnotu s velikostí _X a znaménkem _Y

```cpp
inline float copysignf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu s velikostí _X a znaménkem _Y

## <a name="cos"></a>Cos

Vypočítá kosinus argumentu.

```cpp
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus argumentu.

## <a name="cosf"></a>cosf –

Vypočítá kosinus argumentu.

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus argumentu.

## <a name="cosh"></a>cosh –

Vypočítá hodnotu hyperbolický kosinus argumentu.

```cpp
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolický kosinus argumentu.

## <a name="coshf"></a>coshf –

Vypočítá hodnotu hyperbolický kosinus argumentu.

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolický kosinus argumentu.

## <a name="cospi"></a>cospi –

Vypočítá hodnotu kosinus \* pí _X

```cpp
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus \* pí _X

## <a name="cospif"></a>cospif –

Vypočítá hodnotu kosinus \* pí _X

```cpp
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus \* pí _X

## <a name="erf"></a>ERF

Vypočítá funkci Error _X

```cpp
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí funkci Error pro _X

## <a name="erfc"></a>ERFC –

Vypočítá doplňkovou chybovou funkci _X

```cpp
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí doplňkovou chybovou funkci _X.

## <a name="erfcf"></a>erfcf –

Vypočítá doplňkovou chybovou funkci _X

```cpp
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí doplňkovou chybovou funkci _X.

## <a name="erfcinv"></a>erfcinv –

Vypočítá inverzní funkci doplňkové chyby _X

```cpp
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní funkci doplňkové chyby _X

## <a name="erfcinvf"></a>erfcinvf –

Vypočítá inverzní funkci doplňkové chyby _X

```cpp
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní funkci doplňkové chyby _X

## <a name="erff"></a>erff –

Vypočítá funkci Error _X

```cpp
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí funkci Error pro _X

## <a name="erfinv"></a>erfinv –

Vypočítá funkci invertované chyby _X

```cpp
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí funkci invertující chybu _X

## <a name="erfinvf"></a>erfinvf –

Vypočítá funkci invertované chyby _X

```cpp
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí funkci invertující chybu _X

## <a name="exp10"></a>exp10 –

Vypočítá exponenciální hodnotu argumentu o základu 10.

```cpp
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponenciální hodnotu argumentu o základu 10.

## <a name="exp10f"></a>exp10f –

Vypočítá exponenciální hodnotu argumentu o základu 10.

```cpp
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponenciální hodnotu argumentu o základu 10.

## <a name="expm1"></a>expm1 –

Vypočítá exponenciální funkci argumentu o základu e a odečte 1.

```cpp
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*zmocněn*<br/>
Exponenciální výraz *n* matematického výrazu `e`<sup>n</sup>, kde `e` je základem přirozeného logaritmu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální funkce argumentu o základu e a odečte 1.

## <a name="expm1f"></a>expm1f –

Vypočítá exponenciální funkci argumentu o základu e a odečte 1.

```cpp
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*zmocněn*<br/>
Exponenciální výraz *n* matematického výrazu `e`<sup>n</sup>, kde `e` je základem přirozeného logaritmu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální funkce argumentu o základu e a odečte 1.

## <a name="exp"></a>oček

Vypočítá exponenciální hodnotu argumentu (Base-e).

```cpp
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponenciální hodnotu argumentu (Base-e).

## <a name="expf"></a>expf –

Vypočítá exponenciální hodnotu argumentu (Base-e).

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponenciální hodnotu argumentu (Base-e).

## <a name="exp2"></a>exp2 –

Vypočítá exponenciální hodnotu argumentu o základu 2.

```cpp
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponenciální hodnotu argumentu o základu 2.

## <a name="exp2f"></a>exp2f –

Vypočítá exponenciální hodnotu argumentu o základu 2.

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponenciální hodnotu argumentu o základu 2.

## <a name="fabs"></a>fabs –

Vrátí absolutní hodnotu argumentu.

```cpp
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí absolutní hodnotu argumentu.

## <a name="fabsf"></a>fabsf –

Vrátí absolutní hodnotu argumentu.

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí absolutní hodnotu argumentu.

## <a name="fdim"></a>fdim –

Vypočítá kladný rozdíl mezi argumenty.

```cpp
inline float fdim(
   float _X,
   float _Y
) restrict(amp);
inline double fdim(
   double _X,
   double _Y
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
*_Y* hodnota s plovoucí desetinnou čárkou<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi _X a _Y, pokud _X je větší než _Y; v opačném případě + 0.

## <a name="fdimf"></a>fdimf –

Vypočítá kladný rozdíl mezi argumenty.

```cpp
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
*_Y* hodnota s plovoucí desetinnou čárkou<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi _X a _Y, pokud _X je větší než _Y; v opačném případě + 0.

## <a name="floor"></a>řízení

Vypočítá podlahu argumentu.

```cpp
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí podlahu argumentu.

## <a name="floorf"></a>floorf –

Vypočítá podlahu argumentu.

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí podlahu argumentu.

## <a name="a-namefma-fma"></a><a name="fma"> FMA

Vypočítá součin prvního a druhého zadaného argumentu a potom do výsledku přidá třetí zadaný argument. celý výpočet se provádí jako jediná operace.

```cpp
inline float fma(
   float _X,
   float _Y,
   float _Z
) restrict(amp);

inline double fma(
   double _X,
   double _Y,
   double _Z
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
První argument s plovoucí desetinnou čárkou.
*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.
*_Z*<br/>
Třetí argument s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Výsledek výrazu (_X \* _Y) + _Z. Celý výpočet se provádí jako jediná operace. To znamená, že dílčí výrazy jsou vypočítány na nekonečnou přesnost a pouze konečný výsledek je zaokrouhlen.

## <a name="fmaf"></a>fmaf –

Vypočítá součin prvního a druhého zadaného argumentu a potom do výsledku přidá třetí zadaný argument. celý výpočet se provádí jako jediná operace.

```cpp
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
První argument s plovoucí desetinnou čárkou.
*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.
*_Z*<br/>
Třetí argument s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Výsledek výrazu (_X \* _Y) + _Z. Celý výpočet se provádí jako jediná operace. To znamená, že dílčí výrazy jsou vypočítány na nekonečnou přesnost a pouze konečný výsledek je zaokrouhlen.

## <a name="fmax"></a>Fmax –

Určení maximální číselné hodnoty argumentů

```cpp
inline float fmax(
    float _X,
    float _Y) restrict(amp);

inline double fmax(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí maximální číselnou hodnotu argumentů.

## <a name="fmaxf"></a>fmaxf –

Určení maximální číselné hodnoty argumentů

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí maximální číselnou hodnotu argumentů.

## <a name="fmin"></a>fmin –

Určení minimální číselné hodnoty argumentů

```cpp
inline float fmin(
    float _X,
    float _Y) restrict(amp);

inline double fmin(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí minimální číselnou hodnotu argumentů.

## <a name="fminf"></a>fminf –

Určení minimální číselné hodnoty argumentů

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí minimální číselnou hodnotu argumentů.

## <a name="fmod"></a>fmod – – funkceC++ (amp)

Vypočítá zbytek prvního zadaného argumentu děleného druhým specifikovaným argumentem.

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
První argument s plovoucí desetinnou čárkou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Zbytek `_X` dělený `_Y`; To znamená, že hodnota `_X` - `_Y`*n*, kde *n* je celé číslo, aby velikost `_X` - `_Y`*n* byla menší než velikost `_Y`.

## <a name="fmodf"></a>fmodf –

Vypočítá zbytek prvního zadaného argumentu děleného druhým specifikovaným argumentem.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
První argument s plovoucí desetinnou čárkou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Zbytek `_X` dělený `_Y`; To znamená, že hodnota `_X` - `_Y`*n*, kde *n* je celé číslo, aby velikost `_X` - `_Y`*n* byla menší než velikost `_Y`.

## <a name="fpclassify"></a>fpclassify –

Klasifikuje hodnotu argumentu jako NaN, infinité, normální, mezinormální, nula.

```cpp
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu makra klasifikace čísel odpovídající hodnotě argumentu.

## <a name="frexp"></a>frexp –

Získá mantisu a exponent _X.

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);

inline double frexp(
    double _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Exp*<br/>
Vrátí celočíselný exponent _X v hodnotě s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Vrátí _X mantisy.

## <a name="frexpf"></a>frexpf –

Získá mantisu a exponent _X.

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Exp*<br/>
Vrátí celočíselný exponent _X v hodnotě s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Vrátí _X mantisy.

## <a name="hypot"></a>hypot –

Vypočítá druhou odmocninu součtu čtverců _X a _Y

```cpp
inline float hypot(
    float _X,
    float _Y) restrict(amp);

inline double hypot(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí druhou odmocninu součtu čtverců _X a _Y

## <a name="hypotf"></a>hypotf –

Vypočítá druhou odmocninu součtu čtverců _X a _Y

```cpp
inline float hypotf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí druhou odmocninu součtu čtverců _X a _Y

## <a name="ilogb"></a>ilogb –

Extrahovat exponent _X jako hodnotu se znaménkem int

```cpp
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponent _X jako hodnotu se znaménkem int.

## <a name="ilogbf"></a>ilogbf –

Extrahovat exponent _X jako hodnotu se znaménkem int

```cpp
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponent _X jako hodnotu se znaménkem int.

## <a name="isfinite"></a>isfinite –

Určuje, zda má argument konečnou hodnotu.

```cpp
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu, pokud je argument a jenom v případě, že má argument konečnou hodnotu.

## <a name="isinf"></a>isinf –

Určuje, zda je argumentem nekonečno.

```cpp
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu, pokud je a jenom v případě, že má argument nekonečnou hodnotu.

## <a name="isnan"></a>IsNaN

Určuje, zda je argumentem hodnota NaN.

```cpp
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu, pokud je argument a jenom v případě, že má argument hodnotu NaN.

## <a name="isnormal"></a>isnormal –

Určuje, jestli je argument normální.

```cpp
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu pouze v případě, že argument má normální hodnotu.

## <a name="ldexp"></a>ldexp –

Vypočítá reálné číslo ze zadaného mantisu a exponentu.

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, mantisa

*_Exp*<br/>
Celočíselná hodnota, exponent

### <a name="return-value"></a>Návratová hodnota

Vrátí _X \* 2 ^ _Exp

## <a name="ldexpf"></a>ldexpf –

Vypočítá reálné číslo ze zadaného mantisu a exponentu.

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, mantisa

*_Exp*<br/>
Celočíselná hodnota, exponent

### <a name="return-value"></a>Návratová hodnota

Vrátí _X \* 2 ^ _Exp

## <a name="lgamma"></a>lgamma –

Vypočítá přirozený logaritmus absolutní hodnoty argumentu gamma.

```cpp
inline float lgamma(
    float _X,
    _Out_ int* _Sign) restrict(amp);

inline double lgamma(
    double _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Sign*<br/>
Vrátí znaménko.

### <a name="return-value"></a>Návratová hodnota

Vrátí přirozený logaritmus absolutní hodnoty gama argumentu.

## <a name="lgammaf"></a>lgammaf –

Vypočítá přirozený logaritmus absolutní hodnoty argumentu gamma.

```cpp
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Sign*<br/>
Vrátí znaménko.

### <a name="return-value"></a>Návratová hodnota

Vrátí přirozený logaritmus absolutní hodnoty gama argumentu.

## <a name="log"></a>protokolu

Vypočítá logaritmus argumentu o základu e.

```cpp
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu e.

## <a name="log10"></a>log10 –

Vypočítá logaritmus argumentu o základu 10.

```cpp
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 10.

## <a name="log10f"></a>log10f –

Vypočítá logaritmus argumentu o základu 10.

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 10.

## <a name="log1p"></a>log1p –

Vypočítá logaritmus o základu e hodnoty 1 a argument.

```cpp
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus o základu e hodnoty 1 a argument.

## <a name="log1pf"></a>log1pf –

Vypočítá logaritmus o základu e hodnoty 1 a argument.

```cpp
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus o základu e hodnoty 1 a argument.

## <a name="log2"></a>log2 –

Vypočítá logaritmus argumentu o základu 2.

```cpp
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 10.

## <a name="log2f"></a>log2f –

Vypočítá logaritmus argumentu o základu 2.

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 10.

## <a name="logb"></a>logb –

Extrahuje exponent _X jako celočíselnou hodnotu se znaménkem ve formátu s plovoucí desetinnou čárkou.

```cpp
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsaný exponent _X.

## <a name="logbf"></a>logbf –

Extrahuje exponent _X jako celočíselnou hodnotu se znaménkem ve formátu s plovoucí desetinnou čárkou.

```cpp
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsaný exponent _X.

## <a name="logf"></a>logf –

Vypočítá logaritmus argumentu o základu e.

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu e.

## <a name="modf"></a>modf –

Rozdělí zadaný argument na zlomky a celočíselné části.

```cpp
inline float modf(
    float _X,
    _Out_ float* _Iptr) restrict(amp);

inline double modf(
    double _X,
    _Out_ double* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Iptr*<br/>
mimo Celočíselná část `_X`jako hodnota s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Podepsaná Zlomková část `_X`.

## <a name="modff"></a>modff –

Rozdělí zadaný argument na zlomky a celočíselné části.

```cpp
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Iptr*<br/>
Celočíselná část `_X`jako hodnota s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Vrátí oddepsanou zlomkovou část `_X`.

## <a name="nan"></a>pak

Vrátí tichou hodnotu NaN.

```cpp
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrací tiché NaN, pokud je k dispozici, s obsahem, který je uveden v _X

## <a name="nanf"></a>nanf –

Vrátí tichou hodnotu NaN.

```cpp
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrací tiché NaN, pokud je k dispozici, s obsahem, který je uveden v _X

## <a name="nearbyint"></a>nearbyint –

Zaokrouhlí argument na celočíselnou hodnotu ve formátu s plovoucí desetinnou čárkou pomocí aktuálního směru zaokrouhlení.

```cpp
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí zaokrouhlenou celočíselnou hodnotu.

## <a name="nearbyintf"></a>nearbyintf –

Zaokrouhlí argument na celočíselnou hodnotu ve formátu s plovoucí desetinnou čárkou pomocí aktuálního směru zaokrouhlení.

```cpp
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí zaokrouhlenou celočíselnou hodnotu.

## <a name="nextafter"></a>nextafter –

Určení další reprezentovatelné hodnoty v typu funkce po _X ve směru _Y

```cpp
inline float nextafter(
    float _X,
    float _Y) restrict(amp);

inline double nextafter(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí další reprezentovatelné hodnoty v typu funkce po _X ve směru _Y

## <a name="nextafterf"></a>nextafterf –

Určení další reprezentovatelné hodnoty v typu funkce po _X ve směru _Y

```cpp
inline float nextafterf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí další reprezentovatelné hodnoty v typu funkce po _X ve směru _Y

## <a name="phi"></a>fí

Vrátí kumulativní distribuční funkci argumentu.

```cpp
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kumulativní distribuční funkci argumentu.

## <a name="phif"></a>phif

Vrátí kumulativní distribuční funkci argumentu.

```cpp
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kumulativní distribuční funkci argumentu.

## <a name="pow"></a>log

Vypočítá _X umocněnou mocninou _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, základ

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou, exponent

### <a name="return-value"></a>Návratová hodnota

## <a name="powf"></a>powf –

Vypočítá _X umocněnou mocninou _Y

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, základ

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou, exponent

### <a name="return-value"></a>Návratová hodnota

## <a name="probit"></a>probit

Vrátí funkci inverzní kumulativní distribuce argumentu.

```cpp
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí funkci inverzní kumulativní distribuce argumentu.

## <a name="probitf"></a>probitf

Vrátí funkci inverzní kumulativní distribuce argumentu.

```cpp
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí funkci inverzní kumulativní distribuce argumentu.

## <a name="rcbrt"></a>rcbrt –

Vrátí převrácenou hodnotu z kořene datové krychle argumentu.

```cpp
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí převrácenou hodnotu z kořene datové krychle argumentu.

## <a name="rcbrtf"></a>rcbrtf –

Vrátí převrácenou hodnotu z kořene datové krychle argumentu.

```cpp
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí převrácenou hodnotu z kořene datové krychle argumentu.

## <a name="remainder"></a>Hledáte

Vypočítá zbytek: _X ZBÝV _Y

```cpp
inline float remainder(
    float _X,
    float _Y) restrict(amp);

inline double remainder(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí _X ZBÝV _Y

## <a name="remainderf"></a>remainderf –

Vypočítá zbytek: _X ZBÝV _Y

```cpp
inline float remainderf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí _X ZBÝV _Y

## <a name="remquo"></a>remquo –

Vypočítá zbytek prvního zadaného argumentu děleného druhým specifikovaným argumentem. Vypočítá také podíl mantisa prvního zadaného argumentu děleného mantisa druhého zadaného argumentu a vrátí podíl pomocí umístění zadaného ve třetím argumentu.

```cpp
inline float remquo(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);

inline double remquo(
    double _X,
    double _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
První argument s plovoucí desetinnou čárkou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.

*_Quo*<br/>
mimo Adresa celého čísla, které se používá k vrácení podílu zlomkových bitů `_X` dělený zlomky `_Y`.

### <a name="return-value"></a>Návratová hodnota

Vrátí zbytek `_X` dělený `_Y`.

## <a name="remquof"></a>remquof –

Vypočítá zbytek prvního zadaného argumentu děleného druhým specifikovaným argumentem. Vypočítá také podíl mantisa prvního zadaného argumentu děleného mantisa druhého zadaného argumentu a vrátí podíl pomocí umístění zadaného ve třetím argumentu.

```cpp
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
První argument s plovoucí desetinnou čárkou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.

*_Quo*<br/>
mimo Adresa celého čísla, které se používá k vrácení podílu zlomkových bitů `_X` dělený zlomky `_Y`.

### <a name="return-value"></a>Návratová hodnota

Vrátí zbytek `_X` dělený `_Y`.

## <a name="round"></a>zpoždění

Zaokrouhlí _X na nejbližší celé číslo.

```cpp
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí nejbližší celé číslo _X

## <a name="roundf"></a>roundf –

Zaokrouhlí _X na nejbližší celé číslo.

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí nejbližší celé číslo _X

## <a name="rsqrt"></a>rsqrt –

Vrátí převrácenou druhou odmocninu argumentu.

```cpp
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí převrácenou druhou odmocninu argumentu.

## <a name="rsqrtf"></a>rsqrtf –

Vrátí převrácenou druhou odmocninu argumentu.

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí převrácenou druhou odmocninu argumentu.

## <a name="scalb"></a>scalb –

Vynásobí _X FLT_RADIX _Y napájení.

```cpp
inline float scalb(
    float _X,
    float _Y) restrict(amp);

inline double scalb(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí _X \* (FLT_RADIX ^ _Y).

## <a name="scalbf"></a>scalbf –

Vynásobí _X FLT_RADIX _Y napájení.

```cpp
inline float scalbf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí _X \* (FLT_RADIX ^ _Y).

## <a name="scalbn"></a>scalbn –

Vynásobí _X FLT_RADIX _Y napájení.

```cpp
inline float scalbn(
    float _X,
    int _Y) restrict(amp);

inline double scalbn(
    double _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí _X \* (FLT_RADIX ^ _Y).

## <a name="scalbnf"></a>scalbnf –

Vynásobí _X FLT_RADIX _Y napájení.

```cpp
inline float scalbnf(
    float _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí _X \* (FLT_RADIX ^ _Y).

## <a name="signbit"></a>signbit –

Určuje, zda je znaménko _X záporné.

```cpp
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu, pokud a pouze v případě, že je znaménko _X záporné.

## <a name="signbitf"></a>signbitf –

Určuje, zda je znaménko _X záporné.

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu, pokud a pouze v případě, že je znaménko _X záporné.

## <a name="sin"></a>tlačítek

Vypočítá hodnotu sinus argumentu

```cpp
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu sinus argumentu.

## <a name="sinf"></a>sinf –

Vypočítá hodnotu sinus argumentu

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu sinus argumentu.

## <a name="sincos"></a>sincos –

Vypočítá hodnotu sinus a kosinus _X

```cpp
inline void sincos(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);

inline void sincos(
    double _X,
    _Out_ double* _S,
    _Out_ double* _C) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_S*<br/>
Vrátí hodnotu sinus _X.

*_C*<br/>
Vrátí hodnotu kosinus _X.

## <a name="sincosf"></a>sincosf –

Vypočítá hodnotu sinus a kosinus _X

```cpp
inline void sincosf(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_S*<br/>
Vrátí hodnotu sinus _X.

*_C*<br/>
Vrátí hodnotu kosinus _X.

## <a name="sinh"></a>sinh –

Vypočítá hodnotu hyperbolický sinus argumentu.

```cpp
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolický sinus argumentu.

## <a name="sinhf"></a>sinhf –

Vypočítá hodnotu hyperbolický sinus argumentu.

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolický sinus argumentu.

## <a name="sinpi"></a>sinpi –

Vypočítá hodnotu sinus \* pí _X

```cpp
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu sinus \* pí _X

## <a name="sinpif"></a>sinpif –

Vypočítá hodnotu sinus \* pí _X

```cpp
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu sinus \* pí _X

## <a name="sqrt"></a>SQRT

Vypočítá kořen squre argumentu.

```cpp
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kořen squre argumentu.

## <a name="sqrtf"></a>sqrtf –

Vypočítá kořen squre argumentu.

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kořen squre argumentu.

## <a name="tan"></a>nádrž

Vypočítá hodnotu tangens argumentu.

```cpp
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tangens argumentu.

## <a name="tanf"></a>tanf –

Vypočítá hodnotu tangens argumentu.

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tangens argumentu.

## <a name="tanh"></a>tanh –

Vypočítá hodnotu hyperbolický tangens argumentu.

```cpp
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolický tangens argumentu.

## <a name="tanhf"></a>tanhf –

Vypočítá hodnotu hyperbolický tangens argumentu.

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolický tangens argumentu.

## <a name="tanpi"></a>tanpi –

Vypočítá hodnotu tangens \* pí _X

```cpp
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí tangensovou hodnotu pí \* _X

## <a name="tanpif"></a>tanpif –

Vypočítá hodnotu tangens \* pí _X

```cpp
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí tangensovou hodnotu pí \* _X

## <a name="tgamma"></a>tgamma –

Vypočítá funkci gamma _X

```cpp
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek funkce gamma _X.

## <a name="tgammaf"></a>tgammaf –

Vypočítá funkci gamma _X

```cpp
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek funkce gamma _X.

## <a name="trunc"></a>TRUNC –

Zkrátí argument na celočíselnou komponentu.

```cpp
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí celočíselnou komponentu argumentu.

## <a name="truncf"></a>truncf –

Zkrátí argument na celočíselnou komponentu.

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí celočíselnou komponentu argumentu.

## <a name="see-also"></a>Viz také

[Concurrency::precise_math – obor názvů](concurrency-precise-math-namespace.md)
