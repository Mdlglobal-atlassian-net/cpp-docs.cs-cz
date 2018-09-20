---
title: Funkce oboru názvů Concurrency::precise_math | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dac840ecb0d3dadd25387eebff9c28ff83213cbe
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448529"
---
# <a name="concurrencyprecisemath-namespace-functions"></a>Funkce oboru názvů Concurrency::precise_math

||||
|-|-|-|
|[Funkce ACOS](#acos)|[acosf](#acosf)|[acosh –](#acosh)|
|[acoshf](#acoshf)|[ASIN](#asin)|[asinf –](#asinf)|
|[asinh –](#asinh)|[asinhf –](#asinhf)|[Atan](#atan)|
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf –](#atanf)|
|[atanh –](#atanh)|[atanhf –](#atanhf)|[cbrt](#cbrt)|
|[cbrtf](#cbrtf)|[Ceil –](#ceil)|[ceilf –](#ceilf)|
|[copysign –](#copysign)|[copysignf –](#copysignf)|[Cos](#cos)|
|[cosf](#cosf)|[COSH –](#cosh)|[coshf](#coshf)|
|[cospi](#cospi)|[cospif –](#cospif)|[erf](#erf)|
|[erfc](#erfc)|[erfcf](#erfcf)|[erfcinv –](#erfcinv)|
|[erfcinvf](#erfcinvf)|[erff](#erff)|[erfinv –](#erfinv)|
|[erfinvf –](#erfinvf)|[exp](#exp)|[exp10](#exp10)|
|[exp10f –](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[fabs –](#fabs)|[fabsf –](#fabsf)|[Dolní mez](#floor)|
|[fdim –](#fdim)|[fdimf –](#fdimf)||
|[floorf](#floorf)|[fma](#fma)|[fmaf –](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[Fmin –](#fmin)|[fminf –](#fminf)|[Fmod –](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf](#frexpf)|[hypot –](#hypot)|[hypotf –](#hypotf)|
|[ilogb –](#ilogb)|[ilogbf](#ilogbf)|[isfinite](#isfinite)|
|[isinf –](#isinf)|[isNaN –](#isnan)|[isnormal –](#isnormal)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[protokol](#log)|[log10](#log10)|
|[log10f](#log10f)|[log1p –](#log1p)|[log1pf](#log1pf)|
|[log2](#log2)|[log2f](#log2f)|[logb –](#logb)|
|[logbf –](#logbf)|[logf –](#logf)|[modf –](#modf)|
|[modff](#modff)|[NaN](#nan)|[nanf –](#nanf)|
|[nearbyint –](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter –](#nextafter)|
|[nextafterf](#nextafterf)|[(Phi)](#phi)|[phif –](#phif)|
|[Pow](#pow)|[powf –](#powf)|[probit –](#probit)|
|[probitf](#probitf)|[rcbrt](#rcbrt)|[rcbrtf](#rcbrtf)|
|[Zbývající](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[Zaokrouhlit](#round)|[roundf –](#roundf)|
|[rsqrt –](#rsqrt)|[rsqrtf](#rsqrtf)|[scalb –](#scalb)|
|[scalbf](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit –](#signbit)|[signbitf –](#signbitf)|[Sin](#sin)|
|[sincos –](#sincos)|[sincosf](#sincosf)|[sinf –](#sinf)|
|[SINH –](#sinh)|[sinhf](#sinhf)|[sinpi –](#sinpi)|
|[sinpif –](#sinpif)|[sqrt](#sqrt)|[sqrtf](#sqrtf)|
|[Tan](#tan)|[tanf –](#tanf)|[TANH –](#tanh)|
|[tanhf](#tanhf)|[tanpi –](#tanpi)|[tanpif –](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[TRUNC –](#trunc)|
|[truncf –](#truncf)|

##  <a name="acos"></a>  Funkce ACOS

Vypočítá arkuskosinus argumentu

```
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus kosinus argumentu

##  <a name="acosf"></a>  acosf –

Vypočítá arkuskosinus argumentu

```
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus kosinus argumentu

##  <a name="acosh"></a>  acosh –

Vypočítá inverzní hyperbolický kosinus argumentu

```
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací inverzní hyperbolický kosinus hodnotu argumentu

##  <a name="acoshf"></a>  acoshf –

Vypočítá inverzní hyperbolický kosinus argumentu

```
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací inverzní hyperbolický kosinus hodnotu argumentu

##  <a name="asin"></a>  ASIN

Vypočítá arkussinus argumentu

```
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus sinus argumentu

##  <a name="asinf"></a>  asinf –

Vypočítá arkussinus argumentu

```
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus sinus argumentu

##  <a name="asinh"></a>  asinh –

Vypočte hyperbolický arkussinus argumentu

```
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací inverzní hyperbolický sinus hodnotu argumentu

##  <a name="asinhf"></a>  asinhf –

Vypočte hyperbolický arkussinus argumentu

```
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací inverzní hyperbolický sinus hodnotu argumentu

##  <a name="atan"></a>  Atan

Vypočítá arkustangens argumentu

```
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus tangens argumentu

##  <a name="atan2"></a>  ATAN2

Vypočítá arkustangens výrazu _Y/_X

```
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

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arkustangens výrazu _Y/_X

##  <a name="atan2f"></a>  atan2f –

Vypočítá arkustangens výrazu _Y/_X

```
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arkustangens výrazu _Y/_X

##  <a name="atanf"></a>  atanf –

Vypočítá arkustangens argumentu

```
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus tangens argumentu

##  <a name="atanh"></a>  atanh –

Vypočte hyperbolický arkustangens argumentu

```
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní hodnotu hyperbolického tangentu argumentu

##  <a name="atanhf"></a>  atanhf –

Vypočte hyperbolický arkustangens argumentu

```
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní hodnotu hyperbolického tangentu argumentu

##  <a name="cbrt"></a>  cbrt –

Vypočítá reálné kořenové datové krychle argumentu

```
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí skutečný datové krychle odmocninu argumentu

##  <a name="cbrtf"></a>  cbrtf –

Vypočítá reálné kořenové datové krychle argumentu

```
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí skutečný datové krychle odmocninu argumentu

##  <a name="ceil"></a>  Ceil –

Vypočítá horní mez argumentu

```
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí horní mez argumentu

##  <a name="ceilf"></a>  ceilf –

Vypočítá horní mez argumentu

```
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí horní mez argumentu

##  <a name="copysign"></a>  copysign –

Vytvoří hodnotu s velikost proměnné _X a _y znaménko

```
inline float copysign(
    float _X,
    float _Y) restrict(amp);

inline double copysign(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu s velikost proměnné _X a _y znaménko

##  <a name="copysignf"></a>  copysignf –

Vytvoří hodnotu s velikost proměnné _X a _y znaménko

```
inline float copysignf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu s velikost proměnné _X a _y znaménko

##  <a name="cos"></a>  Cos

Vypočítá kosinus argumentu

```
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus argumentu

##  <a name="cosf"></a>  cosf –

Vypočítá kosinus argumentu

```
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus argumentu

##  <a name="cosh"></a>  COSH –

Vypočítá hodnotu hyperbolického kosinu argumentu

```
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického kosinu argumentu

##  <a name="coshf"></a>  coshf –

Vypočítá hodnotu hyperbolického kosinu argumentu

```
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického kosinu argumentu

##  <a name="cospi"></a>  cospi –

Vypočítá hodnotu kosinus pro číslo pí \* proměnné _X

```
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus pro číslo pí \* proměnné _X

##  <a name="cospif"></a>  cospif –

Vypočítá hodnotu kosinus pro číslo pí \* proměnné _X

```
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus pro číslo pí \* proměnné _X

##  <a name="erf"></a>  ERF –

Vypočítá chybovou funkci proměnné _X

```
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí chybovou funkci proměnné _X

##  <a name="erfc"></a>  ERFC –

Vypočítá doplňkovou chybovou funkci proměnné _X

```
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí doplňkovou chybovou funkci proměnné _X

##  <a name="erfcf"></a>  erfcf –

Vypočítá doplňkovou chybovou funkci proměnné _X

```
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí doplňkovou chybovou funkci proměnné _X

##  <a name="erfcinv"></a>  erfcinv –

Vypočítá inverzní doplňkovou chybovou funkci proměnné _X

```
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní doplňkovou chybovou funkci proměnné _X

##  <a name="erfcinvf"></a>  erfcinvf –

Vypočítá inverzní doplňkovou chybovou funkci proměnné _X

```
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní doplňkovou chybovou funkci proměnné _X

##  <a name="erff"></a>  erff –

Vypočítá chybovou funkci proměnné _X

```
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí chybovou funkci proměnné _X

##  <a name="erfinv"></a>  erfinv –

Vypočítá inverzní chybovou funkci proměnné _X

```
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní chybovou funkci proměnné _X

##  <a name="erfinvf"></a>  erfinvf –

Vypočítá inverzní chybovou funkci proměnné _X

```
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní chybovou funkci proměnné _X

##  <a name="exp10"></a>  exp10 –

Vypočítá základní-10 exponenciálním argumentu

```
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí základní-10 exponenciálním argumentu

##  <a name="exp10f"></a>  exp10f –

Vypočítá základní-10 exponenciálním argumentu

```
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí základní-10 exponenciálním argumentu

##  <a name="expm1"></a>  expm1 –

Vypočítá exponenciální funkci argumentu o základu e a odečte 1.

```
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*Exponent*<br/>
Exponenciální termín *n* matematického výrazu `e` <sup>n</sup>, kde `e` je základ přirozeného logaritmu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální funkce argumentu o základu e a odečte 1.

##  <a name="expm1f"></a>  expm1f –

Vypočítá exponenciální funkci argumentu o základu e a odečte 1.

```
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*Exponent*<br/>
Exponenciální termín *n* matematického výrazu `e` <sup>n</sup>, kde `e` je základ přirozeného logaritmu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální funkce argumentu o základu e a odečte 1.

##  <a name="exp"></a>  Exp

Vypočítá exponenciální funkci argumentu base-e

```
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální funkci argumentu e base

##  <a name="expf"></a>  expf –

Vypočítá exponenciální funkci argumentu base-e

```
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální funkci argumentu e base

##  <a name="exp2"></a>  exp2 –

Vypočítá exponenciální argumentu base-2

```
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální argumentu base-2

##  <a name="exp2f"></a>  exp2f –

Vypočítá exponenciální argumentu base-2

```
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální argumentu base-2

##  <a name="fabs"></a>  fabs –

Vrátí absolutní hodnotu argumentu

```
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí absolutní hodnotu argumentu

##  <a name="fabsf"></a>  fabsf –

Vrátí absolutní hodnotu argumentu

```
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí absolutní hodnotu argumentu

## <a name="fdim"></a> fdim –

Vypočítá pozitivní rozdíl mezi argumenty.
```
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

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou *_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi _X a _Y, pokud je větší než _Y; proměnné _X jinak, + 0.

## <a name="fdimf"></a> fdimf –

Vypočítá pozitivní rozdíl mezi argumenty.
```
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```
### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou *_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi _X a _Y, pokud je větší než _Y; proměnné _X jinak, + 0.

##  <a name="floor"></a>  Dolní mez

Vypočítá dolní mez argumentu

```
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí dolní mez argumentu

##  <a name="floorf"></a>  floorf –

Vypočítá dolní mez argumentu

```
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí dolní mez argumentu

## <a name="a-namefma-fma"></a><a name="fma"> FMA

Vypočítá součin prvního a druhého zadaného argumentu, poté přičte třetí zadaný argument na malá. celý výpočet se provádí jako jediná operace.
```
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

*PROMĚNNÉ _X*<br/>
První argument s plovoucí desetinnou čárkou.
*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.
*_Z*<br/>
Třetí argument s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Výsledek výrazu (_X \* _Y) + _Z. Celý výpočet se provádí jako jediná operace; To znamená že dílčí výrazy se počítají s nekonečnou přesností a pouze konečný výsledek zaokrouhlen.

## <a name="fmaf"></a> fmaf –

Vypočítá součin prvního a druhého zadaného argumentu, poté přičte třetí zadaný argument na malá. celý výpočet se provádí jako jediná operace.
```
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```
### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
První argument s plovoucí desetinnou čárkou.
*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.
*_Z*<br/>
Třetí argument s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Výsledek výrazu (_X \* _Y) + _Z. Celý výpočet se provádí jako jediná operace; To znamená že dílčí výrazy se počítají s nekonečnou přesností a pouze konečný výsledek zaokrouhlen.

##  <a name="fmax"></a>  Fmax –

Určí maximální číselnou hodnotu argumentů

```
inline float fmax(
    float _X,
    float _Y) restrict(amp);

inline double fmax(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátit maximální číselnou hodnotu argumentů

##  <a name="fmaxf"></a>  fmaxf –

Určí maximální číselnou hodnotu argumentů

```
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátit maximální číselnou hodnotu argumentů

##  <a name="fmin"></a>  Fmin –

Určí minimální číselnou hodnotu argumentů

```
inline float fmin(
    float _X,
    float _Y) restrict(amp);

inline double fmin(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátit minimální číselnou hodnotu argumentů

##  <a name="fminf"></a>  fminf –

Určí minimální číselnou hodnotu argumentů

```
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátit minimální číselnou hodnotu argumentů

##  <a name="fmod"></a>  fmod – funkce (C++ AMP)

Vypočítá zbytek z prvního zadaného argumentu děleného podle druhého zadaného argumentu.

```
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
První argument s plovoucí desetinnou čárkou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Zbývající část `_X` dělený `_Y`; to znamená, že hodnota `_X`  -  `_Y` *n*, kde *n* je celé číslo tak, aby velikost `_X`  -  `_Y` *n* je menší než velikost `_Y`.

##  <a name="fmodf"></a>  fmodf –

Vypočítá zbytek z prvního zadaného argumentu děleného podle druhého zadaného argumentu.

```
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
První argument s plovoucí desetinnou čárkou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Zbývající část `_X` dělený `_Y`; to znamená, že hodnota `_X`  -  `_Y` *n*, kde *n* je celé číslo tak, aby velikost `_X`  -  `_Y` *n* je menší než velikost `_Y`.

##  <a name="fpclassify"></a>  fpclassify –

Klasifikuje hodnota argumentu, protože NaN, nekonečné, Normální, subnormal, nula

```
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu čísla – makro klasifikace odpovídající hodnotu argumentu.

##  <a name="frexp"></a>  frexp –

Načte mantisu a exponent proměnné _X

```
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);

inline double frexp(
    double _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Exp*<br/>
Vrátí exponent proměnné _X celé číslo s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X mantisa

##  <a name="frexpf"></a>  frexpf –

Načte mantisu a exponent proměnné _X

```
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Exp*<br/>
Vrátí exponent proměnné _X celé číslo s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X mantisa

##  <a name="hypot"></a>  hypot –

Vypočítá druhou odmocninu součet kvadratických hodnot _X a _Y

```
inline float hypot(
    float _X,
    float _Y) restrict(amp);

inline double hypot(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí druhou odmocninu součet kvadratických hodnot _X a _Y

##  <a name="hypotf"></a>  hypotf –

Vypočítá druhou odmocninu součet kvadratických hodnot _X a _Y

```
inline float hypotf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí druhou odmocninu součet kvadratických hodnot _X a _Y

##  <a name="ilogb"></a>  ilogb –

Extrahovat jako hodnotu podepsaný int exponent proměnné _X

```
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponent proměnné _X jako hodnoty podepsaný int.

##  <a name="ilogbf"></a>  ilogbf –

Extrahovat jako hodnotu podepsaný int exponent proměnné _X

```
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí exponent proměnné _X jako hodnoty podepsaný int.

##  <a name="isfinite"></a>  isfinite –

Určuje, zda má argument konečnou hodnotu

```
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud a pouze pokud má argument konečnou hodnotu

##  <a name="isinf"></a>  isinf –

Určí, zda je argument nekonečno

```
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu pouze v případě má nekonečnou hodnotu argumentu

##  <a name="isnan"></a>  isNaN –

Určí, zda je argument NaN

```
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud a pouze pokud má argument hodnotu NaN

##  <a name="isnormal"></a>  isnormal –

Určí, zda je argument normální

```
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud a pouze pokud má argument běžné hodnoty

##  <a name="ldexp"></a>  ldexp –

Vypočítá reálné číslo z určené mantisy a exponentu.

```
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou, mantisa

*_Exp*<br/>
Celočíselná hodnota, exponent

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X \* 2 ^ _Exp

##  <a name="ldexpf"></a>  ldexpf –

Vypočítá reálné číslo z určené mantisy a exponentu.

```
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou, mantisa

*_Exp*<br/>
Celočíselná hodnota, exponent

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X \* 2 ^ _Exp

##  <a name="lgamma"></a>  lgamma –

Vypočítá absolutní hodnotu argumentu gama přirozený logaritmus

```
inline float lgamma(
    float _X,
    _Out_ int* _Sign) restrict(amp);

inline double lgamma(
    double _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Přihlásit*<br/>
Vrátí znaménko

### <a name="return-value"></a>Návratová hodnota

Vrátí přirozený logaritmus absolutní hodnotu argumentu gama

##  <a name="lgammaf"></a>  lgammaf –

Vypočítá absolutní hodnotu argumentu gama přirozený logaritmus

```
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Přihlásit*<br/>
Vrátí znaménko

### <a name="return-value"></a>Návratová hodnota

Vrátí přirozený logaritmus absolutní hodnotu argumentu gama

##  <a name="log"></a>  protokol

Vypočítá logaritmus argumentu o základu e

```
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu e

##  <a name="log10"></a>  LOG10

Vypočítá logaritmus argumentu o základu 10

```
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 10

##  <a name="log10f"></a>  log10f –

Vypočítá logaritmus argumentu o základu 10

```
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 10

##  <a name="log1p"></a>  log1p –

Vypočítá logaritmus o základu e 1 plus argumentu

```
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus o základu e 1 plus argumentu

##  <a name="log1pf"></a>  log1pf –

Vypočítá logaritmus o základu e 1 plus argumentu

```
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus o základu e 1 plus argumentu

##  <a name="log2"></a>  log2 –

Vypočítá logaritmus argumentu o základu 2

```
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 10

##  <a name="log2f"></a>  log2f –

Vypočítá logaritmus argumentu o základu 2

```
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 10

##  <a name="logb"></a>  logb –

Extrahuje exponent proměnné _X jako celé číslo se znaménkem hodnoty ve formátu s plovoucí desetinnou čárkou

```
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsané exponent proměnné _X

##  <a name="logbf"></a>  logbf –

Extrahuje exponent proměnné _X jako celé číslo se znaménkem hodnoty ve formátu s plovoucí desetinnou čárkou

```
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsané exponent proměnné _X

##  <a name="logf"></a>  logf –

Vypočítá logaritmus argumentu o základu e

```
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu e

##  <a name="modf"></a>  modf –

Rozdělí zadaný argument na frakce a celá čísla.

```
inline float modf(
    float _X,
    _Out_ float* _Iptr) restrict(amp);

inline double modf(
    double _X,
    _Out_ double* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Iptr*<br/>
[out] Celočíselnou část `_X`, jako hodnotu s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Podepsaná desetinná část čísla `_X`.

##  <a name="modff"></a>  modff –

Rozdělí zadaný argument na frakce a celá čísla.

```
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Iptr*<br/>
Celočíselnou část `_X`, jako hodnotu s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsaná desetinná část čísla `_X`.

##  <a name="nan"></a>  NaN

Vrátí tichý NaN

```
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí tichý NaN, je-li k dispozici s obsahem uvedené v proměnné _X

##  <a name="nanf"></a>  nanf –

Vrátí tichý NaN

```
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí tichý NaN, je-li k dispozici s obsahem uvedené v proměnné _X

##  <a name="nearbyint"></a>  nearbyint –

Zaokrouhlí číslo argumentu na celočíselnou hodnotu ve formátu s plovoucí desetinnou čárkou, pomocí aktuálního směr zaokrouhlení.

```
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí zaokrouhlené celočíselnou hodnotu.

##  <a name="nearbyintf"></a>  nearbyintf –

Zaokrouhlí číslo argumentu na celočíselnou hodnotu ve formátu s plovoucí desetinnou čárkou, pomocí aktuálního směr zaokrouhlení.

```
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí zaokrouhlené celočíselnou hodnotu.

##  <a name="nextafter"></a>  nextafter –

Určení v typu funkce následující reprezentovatelnou hodnotu po _X ve směru _y

```
inline float nextafter(
    float _X,
    float _Y) restrict(amp);

inline double nextafter(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí následující reprezentovatelnou hodnotu v typu funkce po _X ve směru _y

##  <a name="nextafterf"></a>  nextafterf –

Určení v typu funkce následující reprezentovatelnou hodnotu po _X ve směru _y

```
inline float nextafterf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí následující reprezentovatelnou hodnotu v typu funkce po _X ve směru _y

##  <a name="phi"></a>  (Phi)

Vrátí kumulativní distribuční funkci argumentu

```
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kumulativní distribuční funkci argumentu

##  <a name="phif"></a>  phif –

Vrátí kumulativní distribuční funkci argumentu

```
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kumulativní distribuční funkci argumentu

##  <a name="pow"></a>  Pow

Vypočítá proměnnou _X umocněnou exponentem _y

```
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou, základní

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou, exponent

### <a name="return-value"></a>Návratová hodnota

##  <a name="powf"></a>  powf –

Vypočítá proměnnou _X umocněnou exponentem _y

```
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou, základní

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou, exponent

### <a name="return-value"></a>Návratová hodnota

##  <a name="probit"></a>  probit –

Vrátí inverzní kumulativní distribuční funkci argumentu

```
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní kumulativní distribuční funkci argumentu

##  <a name="probitf"></a>  probitf –

Vrátí inverzní kumulativní distribuční funkci argumentu

```
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí inverzní kumulativní distribuční funkci argumentu

##  <a name="rcbrt"></a>  rcbrt –

Vrátí převrácenou hodnotu argumentu kořenové datové krychle

```
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí převrácenou hodnotu argumentu kořenové datové krychle

##  <a name="rcbrtf"></a>  rcbrtf –

Vrátí převrácenou hodnotu argumentu kořenové datové krychle

```
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí převrácenou hodnotu argumentu kořenové datové krychle

##  <a name="remainder"></a>  Zbývající

Vypočítá zbytek: _X REM _Y

```
inline float remainder(
    float _X,
    float _Y) restrict(amp);

inline double remainder(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X REM _Y

##  <a name="remainderf"></a>  remainderf –

Vypočítá zbytek: _X REM _Y

```
inline float remainderf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X REM _Y

##  <a name="remquo"></a>  remquo –

Vypočítá zbytek z prvního zadaného argumentu děleného podle druhého zadaného argumentu. Také vypočítá podíl mantisy prvního zadaného argumentu děleného mantisou druhého zadaného argumentu a vrátí podíl pomocí umístění zadaného ve třetím argumentu.

```
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

*PROMĚNNÉ _X*<br/>
První argument s plovoucí desetinnou čárkou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.

*Hodnoty _Quo*<br/>
[out] Adresa celého čísla, který se používá k vrácení podílu zlomkových bitů `_X` dělený dělené desetinnými bity `_Y`.

### <a name="return-value"></a>Návratová hodnota

Vrátí zbytek `_X` dělený `_Y`.

##  <a name="remquof"></a>  remquof –

Vypočítá zbytek z prvního zadaného argumentu děleného podle druhého zadaného argumentu. Také vypočítá podíl mantisy prvního zadaného argumentu děleného mantisou druhého zadaného argumentu a vrátí podíl pomocí umístění zadaného ve třetím argumentu.

```
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
První argument s plovoucí desetinnou čárkou.

*_Y*<br/>
Druhý argument s plovoucí desetinnou čárkou.

*Hodnoty _Quo*<br/>
[out] Adresa celého čísla, který se používá k vrácení podílu zlomkových bitů `_X` dělený dělené desetinnými bity `_Y`.

### <a name="return-value"></a>Návratová hodnota

Vrátí zbytek `_X` dělený `_Y`.

##  <a name="round"></a>  Zaokrouhlit

Zaokrouhlí číslo _X na nejbližší celé číslo.

```
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _x na nejbližší celé číslo

##  <a name="roundf"></a>  roundf –

Zaokrouhlí číslo _X na nejbližší celé číslo.

```
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _x na nejbližší celé číslo

##  <a name="rsqrt"></a>  rsqrt –

Vrátí převrácenou hodnotu druhé odmocniny argumentu

```
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí převrácenou hodnotu druhé odmocniny argumentu

##  <a name="rsqrtf"></a>  rsqrtf –

Vrátí převrácenou hodnotu druhé odmocniny argumentu

```
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí převrácenou hodnotu druhé odmocniny argumentu

##  <a name="scalb"></a>  scalb –

Vynásobí hodnotu proměnné _X tak FLT_RADIX power _Y

```
inline float scalb(
    float _X,
    float _Y) restrict(amp);

inline double scalb(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbf"></a>  scalbf –

Vynásobí hodnotu proměnné _X tak FLT_RADIX power _Y

```
inline float scalbf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbn"></a>  scalbn –

Vynásobí hodnotu proměnné _X tak FLT_RADIX power _Y

```
inline float scalbn(
    float _X,
    int _Y) restrict(amp);

inline double scalbn(
    double _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbnf"></a>  scalbnf –

Vynásobí hodnotu proměnné _X tak FLT_RADIX power _Y

```
inline float scalbnf(
    float _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X \* (FLT_RADIX ^ _Y)

##  <a name="signbit"></a>  signbit –

Určuje, zda je záporné znaménko proměnné _X

```
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud je záporné znaménko proměnné _X

##  <a name="signbitf"></a>  signbitf –

Určuje, zda je záporné znaménko proměnné _X

```
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud je záporné znaménko proměnné _X

##  <a name="sin"></a>  Sin

Vypočítá hodnotu sinu argumentu

```
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu sinu argumentu

##  <a name="sinf"></a>  sinf –

Vypočítá hodnotu sinu argumentu

```
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu sinu argumentu

##  <a name="sincos"></a>  sincos –

Vypočítá hodnotu sinu a kosinu proměnné _x

```
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

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_MALÁ*<br/>
Vrátí sinus hodnotu proměnné _X

*_V*<br/>
Vrátí kosinus hodnotu proměnné _X

##  <a name="sincosf"></a>  sincosf –

Vypočítá hodnotu sinu a kosinu proměnné _x

```
inline void sincosf(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_MALÁ*<br/>
Vrátí sinus hodnotu proměnné _X

*_V*<br/>
Vrátí kosinus hodnotu proměnné _X

##  <a name="sinh"></a>  SINH –

Vypočítá hodnotu hyperbolického sinu argumentu

```
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického sinu argumentu

##  <a name="sinhf"></a>  sinhf –

Vypočítá hodnotu hyperbolického sinu argumentu

```
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického sinu argumentu

##  <a name="sinpi"></a>  sinpi –

Vypočítá hodnotu sinu pí \* proměnné _X

```
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu sinus pro číslo pí \* proměnné _X

##  <a name="sinpif"></a>  sinpif –

Vypočítá hodnotu sinu pí \* proměnné _X

```
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu sinus pro číslo pí \* proměnné _X

##  <a name="sqrt"></a>  Sqrt

Vypočítá kořenové squre argumentu

```
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kořen squre argumentu

##  <a name="sqrtf"></a>  sqrtf –

Vypočítá kořenové squre argumentu

```
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kořen squre argumentu

##  <a name="tan"></a>  Tan

Vypočítá hodnotu tangentu argumentu

```
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tangentu argumentu

##  <a name="tanf"></a>  tanf –

Vypočítá hodnotu tangentu argumentu

```
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tangentu argumentu

##  <a name="tanh"></a>  TANH –

Vypočítá hodnotu hyperbolického tangentu argumentu

```
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického tangentu argumentu

##  <a name="tanhf"></a>  tanhf –

Vypočítá hodnotu hyperbolického tangentu argumentu

```
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického tangentu argumentu

##  <a name="tanpi"></a>  tanpi –

Vypočítá hodnotu tangentu pí \* proměnné _X

```
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tangens pro číslo pí \* proměnné _X

##  <a name="tanpif"></a>  tanpif –

Vypočítá hodnotu tangentu pí \* proměnné _X

```
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tangens pro číslo pí \* proměnné _X

##  <a name="tgamma"></a>  tgamma –

Vypočítá funkce gamma proměnné _x

```
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek funkce gamma proměnné _x

##  <a name="tgammaf"></a>  tgammaf –

Vypočítá funkce gamma proměnné _x

```
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek funkce gamma proměnné _x

##  <a name="trunc"></a>  TRUNC –

Ořízne argument na celé číslo součásti

```
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí komponentu celé číslo argumentu

##  <a name="truncf"></a>  truncf –

Ořízne argument na celé číslo součásti

```
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*PROMĚNNÉ _X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí komponentu celé číslo argumentu

## <a name="see-also"></a>Viz také

[Concurrency::precise_math – obor názvů](concurrency-precise-math-namespace.md)
