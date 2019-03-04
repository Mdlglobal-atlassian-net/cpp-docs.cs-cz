---
title: Funkce oboru názvů Concurrency::fast_math
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math::acos
- amp_math/Concurrency::fast_math::asin
- amp_math/Concurrency::fast_math::asinf
- amp_math/Concurrency::fast_math::atan2
- amp_math/Concurrency::fast_math::atan2f
- amp_math/Concurrency::fast_math::ceil
- amp_math/Concurrency::fast_math::ceilf
- amp_math/Concurrency::fast_math::cosf
- amp_math/Concurrency::fast_math::cosh
- amp_math/Concurrency::fast_math::exp
- amp_math/Concurrency::fast_math::exp2
- amp_math/Concurrency::fast_math::expf
- amp_math/Concurrency::fast_math::fabs
- amp_math/Concurrency::fast_math::floor
- amp_math/Concurrency::fast_math::floorf
- amp_math/Concurrency::fast_math::fmaxf
- amp_math/Concurrency::fast_math::fmin
- amp_math/Concurrency::fast_math::fmod
- amp_math/Concurrency::fast_math::fmodf
- amp_math/Concurrency::fast_math::frexpf
- amp_math/Concurrency::fast_math::isfinite
- amp_math/Concurrency::fast_math::isnan
- amp_math/Concurrency::fast_math::ldexp
- amp_math/Concurrency::fast_math::log
- amp_math/Concurrency::fast_math::log10
- amp_math/Concurrency::fast_math::log2
- amp_math/Concurrency::fast_math::log2f
- amp_math/Concurrency::fast_math::modf
- amp_math/Concurrency::fast_math::modff
- amp_math/Concurrency::fast_math::powf
- amp_math/Concurrency::fast_math::round
- amp_math/Concurrency::fast_math::rsqrt
- amp_math/Concurrency::fast_math::rsqrtf
- amp_math/Concurrency::fast_math::signbitf
- amp_math/Concurrency::fast_math::sin
- amp_math/Concurrency::fast_math::sincosf
- amp_math/Concurrency::fast_math::sinf
- amp_math/Concurrency::fast_math::sinhf
- amp_math/Concurrency::fast_math::sqrt
- amp_math/Concurrency::fast_math::tan
- amp_math/Concurrency::fast_math::tanf
- amp_math/Concurrency::fast_math::tanhf
- amp_math/Concurrency::fast_math::trunc
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
ms.openlocfilehash: 96178ee72073e5063fc009f17ab21565f3cf1ab5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259859"
---
# <a name="concurrencyfastmath-namespace-functions"></a>Funkce oboru názvů Concurrency::fast_math

||||
|-|-|-|
|[acos](#acos)|[acosf](#acosf)|[asin](#asin)|
|[asinf –](#asinf)|[atan](#atan)|[atan2](#atan2)|
|[atan2f](#atan2f)|[atanf –](#atanf)|[ceil](#ceil)|
|[ceilf –](#ceilf)|[cos](#cos)|[cosf](#cosf)|
|[cosh](#cosh)|[coshf](#coshf)|[exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs –](#fabs)|[fabsf –](#fabsf)|[Dolní mez](#floor)|
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[Fmin –](#fmin)|[fminf –](#fminf)|[Fmod –](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf](#frexpf)|
|[isfinite](#isfinite)|[isinf](#isinf)|[isnan](#isnan)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[log](#log)|
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[Pow](#pow)|[powf](#powf)|
|[Zaokrouhlit](#round)|[roundf –](#roundf)|[rsqrt](#rsqrt)|
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[signbitf](#signbitf)|
|[sin](#sin)|[sincos –](#sincos)|[sincosf](#sincosf)|
|[sinf –](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|
|[sqrt](#sqrt)|[sqrtf](#sqrtf)|[Tan](#tan)|
|[tanf –](#tanf)|[tanh](#tanh)|[tanhf](#tanhf)|
|[trunc](#trunc)|[truncf](#truncf)|

##  <a name="acos"></a>  Funkce ACOS

Vypočítá arkuskosinus argumentu

```
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus kosinus argumentu

##  <a name="acosf"></a>  acosf

Vypočítá arkuskosinus argumentu

```
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus kosinus argumentu

##  <a name="asin"></a>  ASIN

Vypočítá arkussinus argumentu

```
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus sinus argumentu

##  <a name="asinf"></a>  asinf –

Vypočítá arkussinus argumentu

```
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus sinus argumentu

##  <a name="atan"></a>  Atan

Vypočítá arkustangens argumentu

```
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus tangens argumentu

##  <a name="atan2"></a>  ATAN2

Vypočítá arkustangens výrazu _Y/_X

```
inline float atan2(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

*_X*<br/>
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

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu arkustangens výrazu _Y/_X

##  <a name="atanf"></a>  atanf –

Vypočítá arkustangens argumentu

```
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu Arkus tangens argumentu

##  <a name="ceil"></a>  ceil

Vypočítá horní mez argumentu

```
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí horní mez argumentu

##  <a name="ceilf"></a>  ceilf –

Vypočítá horní mez argumentu

```
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí horní mez argumentu

##  <a name="cosf"></a>  cosf

Vypočítá kosinus argumentu

```
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus argumentu

##  <a name="coshf"></a>  coshf –

Vypočítá hodnotu hyperbolického kosinu argumentu

```
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického kosinu argumentu

##  <a name="cos"></a>  cos

Vypočítá kosinus argumentu

```
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu kosinus argumentu

##  <a name="cosh"></a>  COSH –

Vypočítá hodnotu hyperbolického kosinu argumentu

```
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického kosinu argumentu

##  <a name="exp"></a>  Exp

Vypočítá exponenciální funkci argumentu base-e

```
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální funkci argumentu e base

##  <a name="exp2"></a>  exp2 –

Vypočítá exponenciální argumentu base-2

```
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální argumentu base-2

##  <a name="exp2f"></a>  exp2f

Vypočítá exponenciální argumentu base-2

```
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální argumentu base-2

##  <a name="expf"></a>  expf

Vypočítá exponenciální funkci argumentu base-e

```
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu exponenciální funkci argumentu e base

##  <a name="fabs"></a>  fabs –

Vrátí absolutní hodnotu argumentu

```
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí absolutní hodnotu argumentu

##  <a name="fabsf"></a>  fabsf –

Vrátí absolutní hodnotu argumentu

```
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí absolutní hodnotu argumentu

##  <a name="floor"></a>  Dolní mez

Vypočítá dolní mez argumentu

```
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí dolní mez argumentu

##  <a name="floorf"></a>  floorf –

Vypočítá dolní mez argumentu

```
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí dolní mez argumentu

##  <a name="fmax"></a>  fmax

Určí maximální číselnou hodnotu argumentů

```
inline float max(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

*_Y*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátit maximální číselnou hodnotu argumentů

##  <a name="fmaxf"></a>  fmaxf

Určí maximální číselnou hodnotu argumentů

```
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

Vrátit maximální číselnou hodnotu argumentů

##  <a name="fmin"></a>  Fmin –

Určí minimální číselnou hodnotu argumentů

```
inline float min(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

*_Y*<br/>
Celočíselná hodnota

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

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátit minimální číselnou hodnotu argumentů

##  <a name="fmod"></a>  Fmod –

Vypočítá zbytek s plovoucí desetinnou čárkou z výrazu _X/_Y

```
inline float fmod(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí zbytek s plovoucí desetinnou čárkou z výrazu _X/_Y

##  <a name="fmodf"></a>  fmodf

Vypočítá zbytek s plovoucí desetinnou čárkou z výrazu _X/_Y.

```
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí zbytek s plovoucí desetinnou čárkou z výrazu _X/_Y

##  <a name="frexp"></a>  frexp –

Načte mantisu a exponent proměnné _X

```
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Exp*<br/>
Vrátí exponent proměnné _X celé číslo s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X mantisa

##  <a name="frexpf"></a>  frexpf

Načte mantisu a exponent proměnné _X

```
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Exp*<br/>
Vrátí exponent proměnné _X celé číslo s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X mantisa

##  <a name="isfinite"></a>  isfinite –

Určuje, zda má argument konečnou hodnotu

```
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud a pouze pokud má argument konečnou hodnotu

##  <a name="isinf"></a>  isinf –

Určí, zda je argument nekonečno

```
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu pouze v případě má nekonečnou hodnotu argumentu

##  <a name="isnan"></a>  isNaN –

Určí, zda je argument NaN

```
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud a pouze pokud má argument hodnotu NaN

##  <a name="ldexp"></a>  ldexp –

Vypočítá reálné číslo z mantisy a exponentu

```
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, mentissa

*_Exp*<br/>
Exponent celé číslo

### <a name="return-value"></a>Návratová hodnota

Returns _X \* 2^_Exp

##  <a name="ldexpf"></a>  ldexpf –

Vypočítá reálné číslo z mantisy a exponentu

```
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, mentissa

*_Exp*<br/>
Exponent celé číslo

### <a name="return-value"></a>Návratová hodnota

Returns _X \* 2^_Exp

##  <a name="log"></a>  protokol

Vypočítá logaritmus argumentu o základu e

```
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu e

##  <a name="log10"></a>  LOG10

Vypočítá logaritmus argumentu o základu 10

```
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 10

##  <a name="log10f"></a>  log10f –

Vypočítá logaritmus argumentu o základu 10

```
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 10

##  <a name="log2"></a>  log2 –

Vypočítá logaritmus argumentu o základu 2

```
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 2

##  <a name="log2f"></a>  log2f –

Vypočítá logaritmus argumentu o základu 2

```
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 10

##  <a name="logf"></a>  logf –

Vypočítá logaritmus argumentu o základu e

```
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu e

##  <a name="modf"></a>  modf

Rozdělí _X na frakce a celá čísla.

```
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Ip*<br/>
Přijímá celočíselnou část hodnoty

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsaná desetinná část proměnné _X

##  <a name="modff"></a>  modff

Rozdělí _X na frakce a celá čísla.

```
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Ip*<br/>
Přijímá celočíselnou část hodnoty

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsaná desetinná část proměnné _X

##  <a name="pow"></a>  Pow

Vypočítá proměnnou _X umocněnou exponentem _y

```
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, základní

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou, exponent

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pro proměnnou _X umocněnou exponentem _y

##  <a name="powf"></a>  powf –

Vypočítá proměnnou _X umocněnou exponentem _y

```
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, základní

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou, exponent

### <a name="return-value"></a>Návratová hodnota

##  <a name="round"></a>  Zaokrouhlit

Zaokrouhlí číslo _X na nejbližší celé číslo.

```
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _x na nejbližší celé číslo

##  <a name="roundf"></a>  roundf –

Zaokrouhlí číslo _X na nejbližší celé číslo.

```
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _x na nejbližší celé číslo

##  <a name="rsqrt"></a>  rsqrt –

Vrátí převrácenou hodnotu druhé odmocniny argumentu

```
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí převrácenou hodnotu druhé odmocniny argumentu

##  <a name="rsqrtf"></a>  rsqrtf

Vrátí převrácenou hodnotu druhé odmocniny argumentu

```
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí převrácenou hodnotu druhé odmocniny argumentu

##  <a name="signbit"></a>  signbit –

Určuje, zda je záporné znaménko proměnné _X

```
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud je záporné znaménko proměnné _X

##  <a name="signbitf"></a>  signbitf –

Určuje, zda je záporné znaménko proměnné _X

```
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud je záporné znaménko proměnné _X

##  <a name="sin"></a>  Sin

Vypočítá hodnotu sinu argumentu

```
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu sinu argumentu

##  <a name="sinf"></a>  sinf –

Vypočítá hodnotu sinu argumentu

```
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu sinu argumentu

##  <a name="sincos"></a>  sincos –

Vypočítá hodnotu sinu a kosinu proměnné _x

```
inline void sincos(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_S*<br/>
Vrátí sinus hodnotu proměnné _X

*_C*<br/>
Vrátí kosinus hodnotu proměnné _X

##  <a name="sincosf"></a>  sincosf –

Vypočítá hodnotu sinu a kosinu proměnné _x

```
inline void sincosf(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

*_S*<br/>
Vrátí sinus hodnotu proměnné _X

*_C*<br/>
Vrátí kosinus hodnotu proměnné _X

##  <a name="sinh"></a>  SINH –

Vypočítá hodnotu hyperbolického sinu argumentu

```
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického sinu argumentu

##  <a name="sinhf"></a>  sinhf –

Vypočítá hodnotu hyperbolického sinu argumentu

```
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického sinu argumentu

##  <a name="sqrt"></a>  Sqrt

Vypočítá kořenové squre argumentu

```
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kořen squre argumentu

##  <a name="sqrtf"></a>  sqrtf –

Vypočítá kořenové squre argumentu

```
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí kořen squre argumentu

##  <a name="tan"></a>  Tan

Vypočítá hodnotu tangentu argumentu

```
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tangentu argumentu

##  <a name="tanf"></a>  tanf

Vypočítá hodnotu tangentu argumentu

```
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu tangentu argumentu

##  <a name="tanh"></a>  TANH –

Vypočítá hodnotu hyperbolického tangentu argumentu

```
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického tangentu argumentu

##  <a name="tanhf"></a>  tanhf –

Vypočítá hodnotu hyperbolického tangentu argumentu

```
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického tangentu argumentu

##  <a name="trunc"></a>  TRUNC –

Ořízne argument na celé číslo součásti

```
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí komponentu celé číslo argumentu

##  <a name="truncf"></a>  truncf –

Ořízne argument na celé číslo součásti

```
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí komponentu celé číslo argumentu

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_math.h **Namespace:** Concurrency::fast_math

## <a name="see-also"></a>Viz také:

[Concurrency::fast_math – obor názvů](concurrency-fast-math-namespace.md)
