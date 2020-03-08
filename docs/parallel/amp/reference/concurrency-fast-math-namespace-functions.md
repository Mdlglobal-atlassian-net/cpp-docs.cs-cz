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
ms.openlocfilehash: 3652e02d9f3ff7b09ee7334dba20188e40344cb5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865467"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Funkce oboru názvů Concurrency::fast_math

||||
|-|-|-|
|[acos](#acos)|[acosf –](#acosf)|[ASIN](#asin)|
|[asinf –](#asinf)|[atan](#atan)|[funkce](#atan2)|
|[atan2f –](#atan2f)|[atanf –](#atanf)|[ceil –](#ceil)|
|[ceilf –](#ceilf)|[Cos](#cos)|[cosf –](#cosf)|
|[cosh –](#cosh)|[coshf –](#coshf)|[oček](#exp)|
|[exp2 –](#exp2)|[exp2f –](#exp2f)|[expf –](#expf)|
|[fabs –](#fabs)|[fabsf –](#fabsf)|[řízení](#floor)|
|[floorf –](#floorf)|[Fmax –](#fmax)|[fmaxf –](#fmaxf)|
|[fmin –](#fmin)|[fminf –](#fminf)|[FMOD –](#fmod)|
|[fmodf –](#fmodf)|[frexp](#frexp)|[frexpf –](#frexpf)|
|[isfinite –](#isfinite)|[isinf](#isinf)|[IsNaN](#isnan)|
|[ldexp](#ldexp)|[ldexpf –](#ldexpf)|[protokolu](#log)|
|[log10 –](#log10)|[log10f –](#log10f)|[log2 –](#log2)|
|[log2f –](#log2f)|[logf –](#logf)|[modf –](#modf)|
|[modff –](#modff)|[log](#pow)|[powf –](#powf)|
|[zpoždění](#round)|[roundf –](#roundf)|[rsqrt –](#rsqrt)|
|[rsqrtf –](#rsqrtf)|[signbit](#signbit)|[signbitf –](#signbitf)|
|[tlačítek](#sin)|[sincos –](#sincos)|[sincosf –](#sincosf)|
|[sinf –](#sinf)|[sinh –](#sinh)|[sinhf –](#sinhf)|
|[SQRT](#sqrt)|[sqrtf –](#sqrtf)|[nádrž](#tan)|
|[tanf –](#tanf)|[tanh –](#tanh)|[tanhf –](#tanhf)|
|[TRUNC –](#trunc)|[truncf –](#truncf)|

## <a name="acos"></a>acos

Vypočítá Arkus kosinus argumentu.

```cpp
inline float acos(float _X) restrict(amp);
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

## <a name="asin"></a>ASIN

Vypočítá Arkus sinus argumentu.

```cpp
inline float asin(float _X) restrict(amp);
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

## <a name="atan"></a>atan

Vypočítá arkustangens argumentu

```cpp
inline float atan(float _X) restrict(amp);
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

## <a name="ceil"></a>ceil –

Vypočítá strop argumentu.

```cpp
inline float ceil(float _X) restrict(amp);
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

## <a name="cos"></a>Cos

Vypočítá kosinus argumentu.

```cpp
inline float cos(float _X) restrict(amp);
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
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hyperbolický kosinus argumentu.

## <a name="exp"></a>oček

Vypočítá exponenciální hodnotu argumentu (Base-e).

```cpp
inline float exp(float _X) restrict(amp);
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

## <a name="fabs"></a>fabs –

Vrátí absolutní hodnotu argumentu.

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

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

## <a name="floor"></a>řízení

Vypočítá podlahu argumentu.

```cpp
inline float floor(float _X) restrict(amp);
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

## <a name="fmax"></a>Fmax –

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

## <a name="fmod"></a>FMOD –

Vypočítá zbytek _X/_Y s plovoucí desetinnou čárkou.

```cpp
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

Vrátí zbytek _X/_Y s plovoucí desetinnou čárkou.

## <a name="fmodf"></a>fmodf –

Vypočítá zbytek _X/_Y s plovoucí desetinnou čárkou.

```cpp
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

Vrátí zbytek _X/_Y s plovoucí desetinnou čárkou.

## <a name="frexp"></a>frexp –

Získá mantisu a exponent _X.

```cpp
inline float frexp(
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

## <a name="isfinite"></a>isfinite –

Určuje, zda má argument konečnou hodnotu.

```cpp
inline int isfinite(float _X) restrict(amp);
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
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu, pokud je argument a jenom v případě, že má argument hodnotu NaN.

## <a name="ldexp"></a>ldexp –

Vypočítá reálné číslo z mantisy a exponentu.

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, mentissa

*_Exp*<br/>
Exponent celého čísla

### <a name="return-value"></a>Návratová hodnota

Vrátí _X \* 2 ^ _Exp

## <a name="ldexpf"></a>ldexpf –

Vypočítá reálné číslo z mantisy a exponentu.

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, mentissa

*_Exp*<br/>
Exponent celého čísla

### <a name="return-value"></a>Návratová hodnota

Vrátí _X \* 2 ^ _Exp

## <a name="log"></a>protokolu

Vypočítá logaritmus argumentu o základu e.

```cpp
inline float log(float _X) restrict(amp);
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

## <a name="log2"></a>log2 –

Vypočítá logaritmus argumentu o základu 2.

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí logaritmus argumentu o základu 2.

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

Rozdělí _X do zlomkové a celočíselné části.

```cpp
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

Vrátí zlomkovou část se znaménkem _X

## <a name="modff"></a>modff –

Rozdělí _X do zlomkové a celočíselné části.

```cpp
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

Vrátí zlomkovou část se znaménkem _X

## <a name="pow"></a>log

Vypočítá _X umocněnou mocninou _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, základ

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou, exponent

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu _X umocněnou mocninou _Y

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

## <a name="round"></a>zpoždění

Zaokrouhlí _X na nejbližší celé číslo.

```cpp
inline float round(float _X) restrict(amp);
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

## <a name="signbit"></a>signbit –

Určuje, zda je znaménko _X záporné.

```cpp
inline int signbit(float _X) restrict(amp);
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
    float* _S,
    float* _C) restrict(amp);
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
    float* _S,
    float* _C) restrict(amp);
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

## <a name="sqrt"></a>SQRT

Vypočítá kořen squre argumentu.

```cpp
inline float sqrt(float _X) restrict(amp);
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

## <a name="trunc"></a>TRUNC –

Zkrátí argument na celočíselnou komponentu.

```cpp
inline float trunc(float _X) restrict(amp);
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

## <a name="requirements"></a>Požadavky

**Header:** amp_math. h **obor názvů:** concurrency:: fast_math

## <a name="see-also"></a>Viz také

[Concurrency::fast_math – obor názvů](concurrency-fast-math-namespace.md)
