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
ms.openlocfilehash: cd0882b072cfe26cd83e63024ae6837dc962ebf9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376401"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Funkce oboru názvů Concurrency::fast_math

||||
|-|-|-|
|[acos](#acos)|[acosf řekl:](#acosf)|[Asin](#asin)|
|[asinf](#asinf)|[Atan](#atan)|[atan2](#atan2)|
|[atan2f](#atan2f)|[atanf](#atanf)|[Ceil](#ceil)|
|[ceilf](#ceilf)|[Protože](#cos)|[cosf řekl:](#cosf)|
|[cosh řekl:](#cosh)|[coshf](#coshf)|[Exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs](#fabs)|[fabsf řekl:](#fabsf)|[Podlaze](#floor)|
|[podlahaf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf](#frexpf)|
|[isfinit](#isfinite)|[isinf](#isinf)|[isnan](#isnan)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[Protokolu](#log)|
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[Pow](#pow)|[powf](#powf)|
|[Kolo](#round)|[roundf](#roundf)|[rsqrt řekl:](#rsqrt)|
|[rsqrtf řekl:](#rsqrtf)|[signbit](#signbit)|[signbitf](#signbitf)|
|[Hřích](#sin)|[sincos](#sincos)|[sincosf](#sincosf)|
|[sinf](#sinf)|[Sinh](#sinh)|[sinhf](#sinhf)|
|[Sqrt](#sqrt)|[sqrtf řekl:](#sqrtf)|[Tan](#tan)|
|[tanf](#tanf)|[tanh](#tanh)|[tanhf (Tanhf)](#tanhf)|
|[Trunc](#trunc)|[truncf](#truncf)|

## <a name="acos"></a><a name="acos"></a>acos

Vypočítá arckosinus argumentu.

```cpp
inline float acos(float _X) restrict(amp);
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

## <a name="asin"></a><a name="asin"></a>Asin

Vypočítá instrůvka argumentu.

```cpp
inline float asin(float _X) restrict(amp);
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

## <a name="atan"></a><a name="atan"></a>Atan

Vypočítá arctangent argumentu.

```cpp
inline float atan(float _X) restrict(amp);
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

## <a name="ceil"></a><a name="ceil"></a>Ceil

Vypočítá strop argumentu

```cpp
inline float ceil(float _X) restrict(amp);
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

## <a name="cos"></a><a name="cos"></a>Protože

Vypočítá kosinus argumentu.

```cpp
inline float cos(float _X) restrict(amp);
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
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolického kosinusu argumentu.

## <a name="exp"></a><a name="exp"></a>Exp

Vypočítá základní exponenciální argument.

```cpp
inline float exp(float _X) restrict(amp);
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

## <a name="fabs"></a><a name="fabs"></a>fabs

Vrátí absolutní hodnotu argumentu.

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

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

## <a name="floor"></a><a name="floor"></a>Podlaze

Vypočítá podlahu argumentu.

```cpp
inline float floor(float _X) restrict(amp);
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

## <a name="fmax"></a><a name="fmax"></a>fmax

Určení maximální číselné hodnoty argumentů

```cpp
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

## <a name="fmod"></a><a name="fmod"></a>fmod

Vypočítá zbytek s plovoucí desetinnou sekundou _X/_Y

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí zbytek s plovoucí desetinnou cínek _X/_Y

## <a name="fmodf"></a><a name="fmodf"></a>fmodf

Vypočítá zbytek s plovoucí desetinnou sekundou _X/_Y.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí zbytek s plovoucí desetinnou cínek _X/_Y

## <a name="frexp"></a><a name="frexp"></a>frexp

Získá mantisu a exponent _X

```cpp
inline float frexp(
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

## <a name="isfinite"></a><a name="isfinite"></a>isfinit

Určuje, zda má argument konečnou hodnotu.

```cpp
inline int isfinite(float _X) restrict(amp);
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
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu pouze v případě, že argument má hodnotu NaN.

## <a name="ldexp"></a><a name="ldexp"></a>Ldexp

Vypočítá reálné číslo z mantisy a exponentu.

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou hodnotou, mentissa

*_Exp*<br/>
Integer exponent

### <a name="return-value"></a>Návratová hodnota

Vrátí \* _X 2^_Exp

## <a name="ldexpf"></a><a name="ldexpf"></a>ldexpf

Vypočítá reálné číslo z mantisy a exponentu.

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou hodnotou, mentissa

*_Exp*<br/>
Integer exponent

### <a name="return-value"></a>Návratová hodnota

Vrátí \* _X 2^_Exp

## <a name="log"></a><a name="log"></a>Protokolu

Vypočítá logaritmus základní hod argumentu.

```cpp
inline float log(float _X) restrict(amp);
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

## <a name="log2"></a><a name="log2"></a>log2

Vypočítá logaritmus základní 2 argumentu.

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus základní-2 argumentu.

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

Rozdělí _X na frakční a celé části.

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Ip*<br/>
Přijme celou část hodnoty.

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsanou zlomkovou část _X

## <a name="modff"></a><a name="modff"></a>modff

Rozdělí _X na frakční a celé části.

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Ip*<br/>
Přijme celou část hodnoty.

### <a name="return-value"></a>Návratová hodnota

Vrátí podepsanou zlomkovou část _X

## <a name="pow"></a><a name="pow"></a>Pow

Vypočítá _X zvýšena na výkon _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou hodnotou, základní

*_Y*<br/>
Hodnota s plovoucí desetinnou hodnotou, exponent

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu _X na výkonnou hodnotu _Y

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

## <a name="round"></a><a name="round"></a>Kolo

Zaokrouhlí _X k nejbližšímu celéčíslo.

```cpp
inline float round(float _X) restrict(amp);
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

## <a name="signbit"></a><a name="signbit"></a>znak

Určuje, zda je znaménko _X záporné.

```cpp
inline int signbit(float _X) restrict(amp);
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
    float* _S,
    float* _C) restrict(amp);
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
    float* _S,
    float* _C) restrict(amp);
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

## <a name="sqrt"></a><a name="sqrt"></a>Sqrt

Vypočítá kořen squre argumentu.

```cpp
inline float sqrt(float _X) restrict(amp);
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

## <a name="trunc"></a><a name="trunc"></a>Trunc

Zkrátí argument na komponentu celé číslo.

```cpp
inline float trunc(float _X) restrict(amp);
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

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_math.h **Obor názvů:** Souběžnost::fast_math

## <a name="see-also"></a>Viz také

[Concurrency::fast_math – obor názvů](concurrency-fast-math-namespace.md)
