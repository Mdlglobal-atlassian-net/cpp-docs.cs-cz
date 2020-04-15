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
ms.openlocfilehash: ee6ab2313fbdc288ebba1b3fdacf192b7b578eb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321859"
---
# <a name="concurrencyprecise_math-namespace-functions"></a>Funkce oboru názvů Concurrency::precise_math

||||
|-|-|-|
|[acos](#acos)|[acosf řekl:](#acosf)|[acosh](#acosh)|
|[acoshf](#acoshf)|[Asin](#asin)|[asinf](#asinf)|
|[asinh](#asinh)|[asinhf](#asinhf)|[Atan](#atan)|
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf](#atanf)|
|[atanh](#atanh)|[atanhf](#atanhf)|[cbrt řekl:](#cbrt)|
|[cbrtf řekl:](#cbrtf)|[Ceil](#ceil)|[ceilf](#ceilf)|
|[copysign](#copysign)|[copysignf](#copysignf)|[Protože](#cos)|
|[cosf řekl:](#cosf)|[cosh řekl:](#cosh)|[coshf](#coshf)|
|[cospi](#cospi)|[cospif](#cospif)|[erf](#erf)|
|[erfc](#erfc)|[erfcf](#erfcf)|[erfcinv](#erfcinv)|
|[erfcinvf](#erfcinvf)|[erff](#erff)|[erfinv](#erfinv)|
|[erfinvf](#erfinvf)|[Exp](#exp)|[exp10](#exp10)|
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[fabs](#fabs)|[fabsf řekl:](#fabsf)|[Podlaze](#floor)|
|[fdim](#fdim)|[fdimf řekl:](#fdimf)||
|[podlahaf](#floorf)|[Fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf](#frexpf)|[hypot](#hypot)|[hypotf](#hypotf)|
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[isfinit](#isfinite)|
|[isinf](#isinf)|[isnan](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[Protokolu](#log)|[log10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[log2](#log2)|[log2f](#log2f)|[logb](#logb)|
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[Nan](#nan)|[nanf](#nanf)|
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[další po](#nextafter)|
|[nextafterf](#nextafterf)|[Phi](#phi)|[phif](#phif)|
|[Pow](#pow)|[powf](#powf)|[probit](#probit)|
|[probitf](#probitf)|[rcbrt řekl:](#rcbrt)|[rcbrtf řekl:](#rcbrtf)|
|[Zbývající část](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[Kolo](#round)|[roundf](#roundf)|
|[rsqrt řekl:](#rsqrt)|[rsqrtf řekl:](#rsqrtf)|[scalb](#scalb)|
|[scalbf](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[signbitf](#signbitf)|[Hřích](#sin)|
|[sincos](#sincos)|[sincosf](#sincosf)|[sinf](#sinf)|
|[Sinh](#sinh)|[sinhf](#sinhf)|[sinpi](#sinpi)|
|[sinpif](#sinpif)|[Sqrt](#sqrt)|[sqrtf řekl:](#sqrtf)|
|[Tan](#tan)|[tanf](#tanf)|[tanh](#tanh)|
|[tanhf (Tanhf)](#tanhf)|[tanpi (Tanpi)](#tanpi)|[tanpif](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[Trunc](#trunc)|
|[truncf](#truncf)|

## <a name="acos"></a><a name="acos"></a>acos

Vypočítá arckosinus argumentu.

```cpp
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arccosine argumentu.

## <a name="acosf"></a><a name="acosf"></a>acosf řekl:

Vypočítá arckosinus argumentu.

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arccosine argumentu.

## <a name="acosh"></a><a name="acosh"></a>acosh

Vypočítá inverzní hyperbolický kosinus argumentu.

```cpp
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní hodnotu hyperbolického kosinusu argumentu.

## <a name="acoshf"></a><a name="acoshf"></a>acoshf

Vypočítá inverzní hyperbolický kosinus argumentu.

```cpp
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní hodnotu hyperbolického kosinusu argumentu.

## <a name="asin"></a><a name="asin"></a>Asin

Vypočítá instrůvka argumentu.

```cpp
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arcsinu argumentu.

## <a name="asinf"></a><a name="asinf"></a>asinf

Vypočítá instrůvka argumentu.

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arcsinu argumentu.

## <a name="asinh"></a><a name="asinh"></a>asinh

Vypočítá inverzní hyperbolický sinus argumentu.

```cpp
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní hyperbolickou hodnotu sinusismu argumentu.

## <a name="asinhf"></a><a name="asinhf"></a>asinhf

Vypočítá inverzní hyperbolický sinus argumentu.

```cpp
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní hyperbolickou hodnotu sinusismu argumentu.

## <a name="atan"></a><a name="atan"></a>Atan

Vypočítá arctangent argumentu.

```cpp
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arctangent argumentu.

## <a name="atan2"></a><a name="atan2"></a>atan2

Vypočítá arctangent _Y/_X

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arctangent _Y/_X

## <a name="atan2f"></a><a name="atan2f"></a>atan2f

Vypočítá arctangent _Y/_X

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arctangent _Y/_X

## <a name="atanf"></a><a name="atanf"></a>atanf

Vypočítá arctangent argumentu.

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arctangent argumentu.

## <a name="atanh"></a><a name="atanh"></a>atanh

Vypočítá inverzní hyperbolickou tečnu argumentu.

```cpp
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní hyperbolickou tečnou hodnotu argumentu.

## <a name="atanhf"></a><a name="atanhf"></a>atanhf

Vypočítá inverzní hyperbolickou tečnu argumentu.

```cpp
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní hyperbolickou tečnou hodnotu argumentu.

## <a name="cbrt"></a><a name="cbrt"></a>cbrt řekl:

Vypočítá skutečný kořen krychle argumentu.

```cpp
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí skutečný kořen krychle argumentu.

## <a name="cbrtf"></a><a name="cbrtf"></a>cbrtf řekl:

Vypočítá skutečný kořen krychle argumentu.

```cpp
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí skutečný kořen krychle argumentu.

## <a name="ceil"></a><a name="ceil"></a>Ceil

Vypočítá strop argumentu

```cpp
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí strop argumentu.

## <a name="ceilf"></a><a name="ceilf"></a>ceilf

Vypočítá strop argumentu

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí strop argumentu.

## <a name="copysign"></a><a name="copysign"></a>copysign

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu s velikostí _X a znaménkem _Y

## <a name="copysignf"></a><a name="copysignf"></a>copysignf

Vytvoří hodnotu s velikostí _X a znaménkem _Y

```cpp
inline float copysignf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu s velikostí _X a znaménkem _Y

## <a name="cos"></a><a name="cos"></a>Protože

Vypočítá kosinus argumentu.

```cpp
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus argumentu.

## <a name="cosf"></a><a name="cosf"></a>cosf řekl:

Vypočítá kosinus argumentu.

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus argumentu.

## <a name="cosh"></a><a name="cosh"></a>cosh řekl:

Vypočítá hyperbolickou kosinusovou hodnotu argumentu.

```cpp
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického kosinusu argumentu.

## <a name="coshf"></a><a name="coshf"></a>coshf

Vypočítá hyperbolickou kosinusovou hodnotu argumentu.

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického kosinusu argumentu.

## <a name="cospi"></a><a name="cospi"></a>cospi

Vypočítá kosinusovou hodnotu \* pi _X

```cpp
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinusu _X \*

## <a name="cospif"></a><a name="cospif"></a>cospif

Vypočítá kosinusovou hodnotu \* pi _X

```cpp
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinusu _X \*

## <a name="erf"></a><a name="erf"></a>erf

Vypočítá chybovou funkci _X

```cpp
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí chybovou funkci _X

## <a name="erfc"></a><a name="erfc"></a>erfc

Vypočítá doplňkovou chybovou funkci _X

```cpp
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí doplňkovou chybovou funkci _X

## <a name="erfcf"></a><a name="erfcf"></a>erfcf

Vypočítá doplňkovou chybovou funkci _X

```cpp
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí doplňkovou chybovou funkci _X

## <a name="erfcinv"></a><a name="erfcinv"></a>erfcinv

Vypočítá inverzní doplňkovou chybovou funkci _X

```cpp
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí funkci inverzní doplňkové chyby _X

## <a name="erfcinvf"></a><a name="erfcinvf"></a>erfcinvf

Vypočítá inverzní doplňkovou chybovou funkci _X

```cpp
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí funkci inverzní doplňkové chyby _X

## <a name="erff"></a><a name="erff"></a>erff

Vypočítá chybovou funkci _X

```cpp
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí chybovou funkci _X

## <a name="erfinv"></a><a name="erfinv"></a>erfinv

Vypočítá funkci inverzní chyby _X

```cpp
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí funkci inverzní chyby _X

## <a name="erfinvf"></a><a name="erfinvf"></a>erfinvf

Vypočítá funkci inverzní chyby _X

```cpp
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí funkci inverzní chyby _X

## <a name="exp10"></a><a name="exp10"></a>exp10

Vypočítá základní 10 exponenciální argument

```cpp
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu základní 10 exponenciální argumentu.

## <a name="exp10f"></a><a name="exp10f"></a>exp10f

Vypočítá základní 10 exponenciální argument

```cpp
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu základní 10 exponenciální argumentu.

## <a name="expm1"></a><a name="expm1"></a>expm1

Vypočítá exponenciální funkci argumentu o základu e a odečte 1.

```cpp
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*Exponent*<br/>
Exponenciální termín *n* matematického `e` <sup>n</sup>výrazu `e` n , kde je základem přirozeného logaritmu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální funkce argumentu o základu e a odečte 1.

## <a name="expm1f"></a><a name="expm1f"></a>expm1f

Vypočítá exponenciální funkci argumentu o základu e a odečte 1.

```cpp
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*Exponent*<br/>
Exponenciální termín *n* matematického `e` <sup>n</sup>výrazu `e` n , kde je základem přirozeného logaritmu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální funkce argumentu o základu e a odečte 1.

## <a name="exp"></a><a name="exp"></a>Exp

Vypočítá základní exponenciální argument.

```cpp
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponenciální hodnotu argumentu base-e.

## <a name="expf"></a><a name="expf"></a>expf

Vypočítá základní exponenciální argument.

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponenciální hodnotu argumentu base-e.

## <a name="exp2"></a><a name="exp2"></a>exp2

Vypočítá základní 2 exponenciální argumentu.

```cpp
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu základu 2 argumentu.

## <a name="exp2f"></a><a name="exp2f"></a>exp2f

Vypočítá základní 2 exponenciální argumentu.

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu základu 2 argumentu.

## <a name="fabs"></a><a name="fabs"></a>fabs

Vrátí absolutní hodnotu argumentu.

```cpp
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí absolutní hodnotu argumentu.

## <a name="fabsf"></a><a name="fabsf"></a>fabsf řekl:

Vrátí absolutní hodnotu argumentu.

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí absolutní hodnotu argumentu.

## <a name="fdim"></a><a name="fdim"></a>fdim

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
_Y hodnoty s plovoucí desetinnou *hodnotou*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi _X a _Y, pokud je _X větší než _Y; jinak +0.

## <a name="fdimf"></a><a name="fdimf"></a>fdimf řekl:

Vypočítá kladný rozdíl mezi argumenty.

```cpp
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
_Y hodnoty s plovoucí desetinnou *hodnotou*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi _X a _Y, pokud je _X větší než _Y; jinak +0.

## <a name="floor"></a><a name="floor"></a>Podlaze

Vypočítá podlahu argumentu.

```cpp
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí podlahu argumentu.

## <a name="floorf"></a><a name="floorf"></a>podlahaf

Vypočítá podlahu argumentu.

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí podlahu argumentu.

## <a name="a-namefma-fma"></a><a name="fma">Fma

Vypočítá součin prvního a druhého zadaného argumentu a potom přidá třetí zadaný argument k výsledku; celý výpočt se provádí jako jedna operace.

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
První argument s plovoucí desetinnou desetinnou desetinnou hlavou.
*_Y*<br/>
Druhý argument s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou deset
*_Z*<br/>
Třetí argument s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou deset

### <a name="return-value"></a>Návratová hodnota

Výsledek výrazu (_X \* _Y) + _Z. Celý výpočt se provádí jako jedna operace; to znamená, že dílčí výrazy jsou vypočteny na nekonečnou přesnost a pouze konečný výsledek je zaokrouhlen.

## <a name="fmaf"></a><a name="fmaf"></a>fmaf

Vypočítá součin prvního a druhého zadaného argumentu a potom přidá třetí zadaný argument k výsledku; celý výpočt se provádí jako jedna operace.

```cpp
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
První argument s plovoucí desetinnou desetinnou desetinnou hlavou.
*_Y*<br/>
Druhý argument s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou deset
*_Z*<br/>
Třetí argument s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou deset

### <a name="return-value"></a>Návratová hodnota

Výsledek výrazu (_X \* _Y) + _Z. Celý výpočt se provádí jako jedna operace; to znamená, že dílčí výrazy jsou vypočteny na nekonečnou přesnost a pouze konečný výsledek je zaokrouhlen.

## <a name="fmax"></a><a name="fmax"></a>fmax

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí maximální číselnou hodnotu argumentů.

## <a name="fmaxf"></a><a name="fmaxf"></a>fmaxf

Určení maximální číselné hodnoty argumentů

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí maximální číselnou hodnotu argumentů.

## <a name="fmin"></a><a name="fmin"></a>fmin

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí minimální číselnou hodnotu argumentů.

## <a name="fminf"></a><a name="fminf"></a>fminf

Určení minimální číselné hodnoty argumentů

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí minimální číselnou hodnotu argumentů.

## <a name="fmod-function-c-amp"></a><a name="fmod"></a>Funkce fmod (C++ AMP)

Vypočítá zbytek prvního zadaného argumentu dělený druhým zadaným argumentem.

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
První argument s plovoucí desetinnou desetinnou desetinnou hlavou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou deset

### <a name="return-value"></a>Návratová hodnota

Zbývající část `_X` vydělená `_Y`; to znamená hodnotu `_X`  -  `_Y` *n*, kde *n* je celé celé `_X`  -  `_Y`číslo tak, že `_Y`velikost *n* je menší než velikost .

## <a name="fmodf"></a><a name="fmodf"></a>fmodf

Vypočítá zbytek prvního zadaného argumentu dělený druhým zadaným argumentem.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
První argument s plovoucí desetinnou desetinnou desetinnou hlavou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou deset

### <a name="return-value"></a>Návratová hodnota

Zbývající část `_X` vydělená `_Y`; to znamená hodnotu `_X`  -  `_Y` *n*, kde *n* je celé celé `_X`  -  `_Y`číslo tak, že `_Y`velikost *n* je menší než velikost .

## <a name="fpclassify"></a><a name="fpclassify"></a>fpclassify

Klasifikuje hodnotu argumentu jako NaN, nekonečná, normální, podnormální, nulová

```cpp
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu makra klasifikace čísel odpovídající hodnotě argumentu.

## <a name="frexp"></a><a name="frexp"></a>frexp

Získá mantisu a exponent _X

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Exp*<br/>
Vrátí celočíselný exponent _X v hodnotě s plovoucí desetinnou desetinnou hodnotou.

### <a name="return-value"></a>Návratová hodnota

Vrátí _X mantisy.

## <a name="frexpf"></a><a name="frexpf"></a>frexpf

Získá mantisu a exponent _X

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Exp*<br/>
Vrátí celočíselný exponent _X v hodnotě s plovoucí desetinnou desetinnou hodnotou.

### <a name="return-value"></a>Návratová hodnota

Vrátí _X mantisy.

## <a name="hypot"></a><a name="hypot"></a>hypot

Vypočítá druhou odmocninu součtu druhých mocnin _X a _Y

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí druhou odmocninu součtu druhých mocnin _X a _Y

## <a name="hypotf"></a><a name="hypotf"></a>hypotf

Vypočítá druhou odmocninu součtu druhých mocnin _X a _Y

```cpp
inline float hypotf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí druhou odmocninu součtu druhých mocnin _X a _Y

## <a name="ilogb"></a><a name="ilogb"></a>ilogb

Extrahovat exponent _X jako podepsanou int hodnotu

```cpp
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponent _X jako podepsanou int hodnotu.

## <a name="ilogbf"></a><a name="ilogbf"></a>ilogbf

Extrahovat exponent _X jako podepsanou int hodnotu

```cpp
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponent _X jako podepsanou int hodnotu.

## <a name="isfinite"></a><a name="isfinite"></a>isfinit

Určuje, zda má argument konečnou hodnotu.

```cpp
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nenulové hodnoty pouze v případě, že argument má konečnou hodnotu.

## <a name="isinf"></a><a name="isinf"></a>isinf

Určuje, zda je argument nekonečnem.

```cpp
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nenulové hodnoty pouze v případě, že argument má nekonečnou hodnotu.

## <a name="isnan"></a><a name="isnan"></a>isnan

Určuje, zda je argument eman.

```cpp
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu pouze v případě, že argument má hodnotu NaN.

## <a name="isnormal"></a><a name="isnormal"></a>je normální

Určuje, zda je argument normální.

```cpp
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nenulové hodnoty pouze v případě, že argument má normální hodnotu.

## <a name="ldexp"></a><a name="ldexp"></a>Ldexp

Vypočítá reálné číslo ze zadané mantisy a exponentu.

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
Hodnota s plovoucí desetinnou hodnotou, mantisa

*_Exp*<br/>
Celá hodnota, exponent

### <a name="return-value"></a>Návratová hodnota

Vrátí \* _X 2^_Exp

## <a name="ldexpf"></a><a name="ldexpf"></a>ldexpf

Vypočítá reálné číslo ze zadané mantisy a exponentu.

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou hodnotou, mantisa

*_Exp*<br/>
Celá hodnota, exponent

### <a name="return-value"></a>Návratová hodnota

Vrátí \* _X 2^_Exp

## <a name="lgamma"></a><a name="lgamma"></a>lgamma

Vypočítá přirozený logaritmus absolutní hodnoty gama argumentu.

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Sign*<br/>
Vrátí znaménko.

### <a name="return-value"></a>Návratová hodnota

Vrátí přirozený logaritmus absolutní hodnoty gama argumentu.

## <a name="lgammaf"></a><a name="lgammaf"></a>lgammaf

Vypočítá přirozený logaritmus absolutní hodnoty gama argumentu.

```cpp
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Sign*<br/>
Vrátí znaménko.

### <a name="return-value"></a>Návratová hodnota

Vrátí přirozený logaritmus absolutní hodnoty gama argumentu.

## <a name="log"></a><a name="log"></a>Protokolu

Vypočítá logaritmus základní hod argumentu.

```cpp
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus základního e argumentu.

## <a name="log10"></a><a name="log10"></a>log10

Vypočítá logaritmus základní 10 argumentu.

```cpp
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus základní-10 argumentu.

## <a name="log10f"></a><a name="log10f"></a>log10f

Vypočítá logaritmus základní 10 argumentu.

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus základní-10 argumentu.

## <a name="log1p"></a><a name="log1p"></a>log1p

Vypočítá logaritmus základní hod 1 plus argument.

```cpp
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus base-e 1 plus argument.

## <a name="log1pf"></a><a name="log1pf"></a>log1pf

Vypočítá logaritmus základní hod 1 plus argument.

```cpp
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus base-e 1 plus argument.

## <a name="log2"></a><a name="log2"></a>log2

Vypočítá logaritmus základní 2 argumentu.

```cpp
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus základní-10 argumentu.

## <a name="log2f"></a><a name="log2f"></a>log2f

Vypočítá logaritmus základní 2 argumentu.

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus základní-10 argumentu.

## <a name="logb"></a><a name="logb"></a>logb

Extrahuje exponent _X jako podepsanou celočíselnou hodnotu ve formátu s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou.

```cpp
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsaný exponent _X

## <a name="logbf"></a><a name="logbf"></a>logbf

Extrahuje exponent _X jako podepsanou celočíselnou hodnotu ve formátu s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou.

```cpp
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsaný exponent _X

## <a name="logf"></a><a name="logf"></a>logf

Vypočítá logaritmus základní hod argumentu.

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus základního e argumentu.

## <a name="modf"></a><a name="modf"></a>modf

Rozdělí zadaný argument na zlomkové a celé části.

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Iptr*<br/>
[out] Celočíselná část `_X`, jako hodnota s plovoucí desetinnou hodnotou.

### <a name="return-value"></a>Návratová hodnota

Podepsaná zlomková `_X`část .

## <a name="modff"></a><a name="modff"></a>modff

Rozdělí zadaný argument na zlomkové a celé části.

```cpp
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Iptr*<br/>
Celočíselná část `_X`, jako hodnota s plovoucí desetinnou hodnotou.

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsanou zlomkovou část souboru `_X`.

## <a name="nan"></a><a name="nan"></a>Nan

Vrátí tichou NaN.

```cpp
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí tichý NaN, je-li k dispozici, s obsahem uvedeným v _X

## <a name="nanf"></a><a name="nanf"></a>nanf

Vrátí tichou NaN.

```cpp
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí tichý NaN, je-li k dispozici, s obsahem uvedeným v _X

## <a name="nearbyint"></a><a name="nearbyint"></a>nearbyint

Zaokrouhlí argument na celočíselnou hodnotu ve formátu s plovoucí desetinnou desetinnou tácek pomocí aktuálního směru zaokrouhlení.

```cpp
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu zaokrouhleného celého čísla.

## <a name="nearbyintf"></a><a name="nearbyintf"></a>nearbyintf

Zaokrouhlí argument na celočíselnou hodnotu ve formátu s plovoucí desetinnou desetinnou tácek pomocí aktuálního směru zaokrouhlení.

```cpp
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu zaokrouhleného celého čísla.

## <a name="nextafter"></a><a name="nextafter"></a>další po

Určete další reprezentovathodnotu v typu funkce po _X ve směru _Y

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí další reprezentovat hodnotu v typu funkce po _X ve směru _Y

## <a name="nextafterf"></a><a name="nextafterf"></a>nextafterf

Určete další reprezentovathodnotu v typu funkce po _X ve směru _Y

```cpp
inline float nextafterf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí další reprezentovat hodnotu v typu funkce po _X ve směru _Y

## <a name="phi"></a><a name="phi"></a>Phi

Vrátí kumulativní distribuční funkci argumentu.

```cpp
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí kumulativní distribuční funkci argumentu.

## <a name="phif"></a><a name="phif"></a>phif

Vrátí kumulativní distribuční funkci argumentu.

```cpp
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí kumulativní distribuční funkci argumentu.

## <a name="pow"></a><a name="pow"></a>Pow

Vypočítá _X zvýšena na výkon _Y

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
Hodnota s plovoucí desetinnou hodnotou, základní

*_Y*<br/>
Hodnota s plovoucí desetinnou hodnotou, exponent

### <a name="return-value"></a>Návratová hodnota

## <a name="powf"></a><a name="powf"></a>powf

Vypočítá _X zvýšena na výkon _Y

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou hodnotou, základní

*_Y*<br/>
Hodnota s plovoucí desetinnou hodnotou, exponent

### <a name="return-value"></a>Návratová hodnota

## <a name="probit"></a><a name="probit"></a>probit

Vrátí inverzní kumulativní distribuční funkci argumentu.

```cpp
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní kumulativní distribuční funkci argumentu.

## <a name="probitf"></a><a name="probitf"></a>probitf

Vrátí inverzní kumulativní distribuční funkci argumentu.

```cpp
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní kumulativní distribuční funkci argumentu.

## <a name="rcbrt"></a><a name="rcbrt"></a>rcbrt řekl:

Vrátí reciproční hodnotu kořene krychle argumentu.

```cpp
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí reciproční hodnotu kořene krychle argumentu.

## <a name="rcbrtf"></a><a name="rcbrtf"></a>rcbrtf řekl:

Vrátí reciproční hodnotu kořene krychle argumentu.

```cpp
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí reciproční hodnotu kořene krychle argumentu.

## <a name="remainder"></a><a name="remainder"></a>Zbývající část

Vypočítá zbytek: _X REM _Y

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí _X REM _Y

## <a name="remainderf"></a><a name="remainderf"></a>remainderf

Vypočítá zbytek: _X REM _Y

```cpp
inline float remainderf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí _X REM _Y

## <a name="remquo"></a><a name="remquo"></a>remquo

Vypočítá zbytek prvního zadaného argumentu dělený druhým zadaným argumentem. Také vypočítá podíl significand první zadaný argument děleno significand druhého zadaného argumentu a vrátí podíl pomocí umístění zadaného ve třetím argumentu.

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
První argument s plovoucí desetinnou desetinnou desetinnou hlavou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou deset

*_Quo*<br/>
[out] Adresa celého čísla, která se používá k vrácení kvocientu `_X` zlomkových bitů děleno zlomkovými bity `_Y`.

### <a name="return-value"></a>Návratová hodnota

Vrátí zbytek `_X` vydělený . `_Y`

## <a name="remquof"></a><a name="remquof"></a>remquof

Vypočítá zbytek prvního zadaného argumentu dělený druhým zadaným argumentem. Také vypočítá podíl significand první zadaný argument děleno significand druhého zadaného argumentu a vrátí podíl pomocí umístění zadaného ve třetím argumentu.

```cpp
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
První argument s plovoucí desetinnou desetinnou desetinnou hlavou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou deset

*_Quo*<br/>
[out] Adresa celého čísla, která se používá k vrácení kvocientu `_X` zlomkových bitů děleno zlomkovými bity `_Y`.

### <a name="return-value"></a>Návratová hodnota

Vrátí zbytek `_X` vydělený . `_Y`

## <a name="round"></a><a name="round"></a>Kolo

Zaokrouhlí _X k nejbližšímu celéčíslo.

```cpp
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí nejbližší celé číslo _X

## <a name="roundf"></a><a name="roundf"></a>roundf

Zaokrouhlí _X k nejbližšímu celéčíslo.

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí nejbližší celé číslo _X

## <a name="rsqrt"></a><a name="rsqrt"></a>rsqrt řekl:

Vrátí reciproční hodnotu druhou odmocninu argumentu.

```cpp
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí reciproční hodnotu druhou odmocninu argumentu.

## <a name="rsqrtf"></a><a name="rsqrtf"></a>rsqrtf řekl:

Vrátí reciproční hodnotu druhou odmocninu argumentu.

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí reciproční hodnotu druhou odmocninu argumentu.

## <a name="scalb"></a><a name="scalb"></a>scalb

Vynásobí _X FLT_RADIX na _Y napájení.

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí \* _X (FLT_RADIX ^ _Y)

## <a name="scalbf"></a><a name="scalbf"></a>scalbf

Vynásobí _X FLT_RADIX na _Y napájení.

```cpp
inline float scalbf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí \* _X (FLT_RADIX ^ _Y)

## <a name="scalbn"></a><a name="scalbn"></a>scalbn

Vynásobí _X FLT_RADIX na _Y napájení.

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí \* _X (FLT_RADIX ^ _Y)

## <a name="scalbnf"></a><a name="scalbnf"></a>scalbnf

Vynásobí _X FLT_RADIX na _Y napájení.

```cpp
inline float scalbnf(
    float _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí \* _X (FLT_RADIX ^ _Y)

## <a name="signbit"></a><a name="signbit"></a>znak

Určuje, zda je znaménko _X záporné.

```cpp
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu pouze v případě, že znaménko _X je záporné.

## <a name="signbitf"></a><a name="signbitf"></a>signbitf

Určuje, zda je znaménko _X záporné.

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu pouze v případě, že znaménko _X je záporné.

## <a name="sin"></a><a name="sin"></a>Hřích

Vypočítá sinusovou hodnotu argumentu.

```cpp
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí sinusovou hodnotu argumentu.

## <a name="sinf"></a><a name="sinf"></a>sinf

Vypočítá sinusovou hodnotu argumentu.

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí sinusovou hodnotu argumentu.

## <a name="sincos"></a><a name="sincos"></a>sincos

Vypočítá sinusa a kosinusová hodnota _X

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
Hodnota s plovoucí desetinnou tálicí hodnotou

*_S*<br/>
Vrátí sinusovou hodnotu _X

*_C*<br/>
Vrátí hodnotu kosinusu _X

## <a name="sincosf"></a><a name="sincosf"></a>sincosf

Vypočítá sinusa a kosinusová hodnota _X

```cpp
inline void sincosf(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_S*<br/>
Vrátí sinusovou hodnotu _X

*_C*<br/>
Vrátí hodnotu kosinusu _X

## <a name="sinh"></a><a name="sinh"></a>Sinh

Vypočítá hyperbolickou sinusovou hodnotu argumentu.

```cpp
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického sinusismu argumentu.

## <a name="sinhf"></a><a name="sinhf"></a>sinhf

Vypočítá hyperbolickou sinusovou hodnotu argumentu.

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického sinusismu argumentu.

## <a name="sinpi"></a><a name="sinpi"></a>sinpi

Vypočítá sinusovou hodnotu pí \* _X

```cpp
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí sinusovou \* hodnotu pí _X

## <a name="sinpif"></a><a name="sinpif"></a>sinpif

Vypočítá sinusovou hodnotu pí \* _X

```cpp
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí sinusovou \* hodnotu pí _X

## <a name="sqrt"></a><a name="sqrt"></a>Sqrt

Vypočítá kořen squre argumentu.

```cpp
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí kořenový adresář argumentu.

## <a name="sqrtf"></a><a name="sqrtf"></a>sqrtf řekl:

Vypočítá kořen squre argumentu.

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí kořenový adresář argumentu.

## <a name="tan"></a><a name="tan"></a>Tan

Vypočítá hodnotu tečny argumentu.

```cpp
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tečny argumentu.

## <a name="tanf"></a><a name="tanf"></a>tanf

Vypočítá hodnotu tečny argumentu.

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tečny argumentu.

## <a name="tanh"></a><a name="tanh"></a>tanh

Vypočítá hyperbolickou tečnou hodnotu argumentu.

```cpp
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolické tečny argumentu.

## <a name="tanhf"></a><a name="tanhf"></a>tanhf (Tanhf)

Vypočítá hyperbolickou tečnou hodnotu argumentu.

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolické tečny argumentu.

## <a name="tanpi"></a><a name="tanpi"></a>tanpi (Tanpi)

Vypočítá hodnotu tečné \* hodnoty pí _X

```cpp
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tečné \* hodnoty pi _X

## <a name="tanpif"></a><a name="tanpif"></a>tanpif

Vypočítá hodnotu tečné \* hodnoty pí _X

```cpp
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tečné \* hodnoty pi _X

## <a name="tgamma"></a><a name="tgamma"></a>tgamma

Vypočítá funkci gama _X

```cpp
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek funkce gama _X

## <a name="tgammaf"></a><a name="tgammaf"></a>tgammaf

Vypočítá funkci gama _X

```cpp
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek funkce gama _X

## <a name="trunc"></a><a name="trunc"></a>Trunc

Zkrátí argument na komponentu celé číslo.

```cpp
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí celou část argumentu.

## <a name="truncf"></a><a name="truncf"></a>truncf

Zkrátí argument na komponentu celé číslo.

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí celou část argumentu.

## <a name="see-also"></a>Viz také

[Souběžnost::precise_math Obor názvů](concurrency-precise-math-namespace.md)
