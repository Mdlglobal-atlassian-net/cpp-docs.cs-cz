---
title: Concurrency::precise_math – obor názvů funkce | Microsoft Docs
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
ms.openlocfilehash: 31648a07ff09ba5babebda06407ccade6a5d8fad
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="concurrencyprecisemath-namespace-functions"></a>Funkce Concurrency::precise_math – obor názvů
||||  
|-|-|-|  
|[ACOS](#acos)|[acosf](#acosf)|[acosh –](#acosh)|  
|[acoshf](#acoshf)|[ASIN](#asin)|[asinf –](#asinf)|  
|[asinh –](#asinh)|[asinhf –](#asinhf)|[Atan](#atan)|  
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf –](#atanf)|  
|[atanh –](#atanh)|[atanhf –](#atanhf)|[cbrt](#cbrt)|  
|[cbrtf](#cbrtf)|[ceil](#ceil)|[ceilf –](#ceilf)|  
|[copysign –](#copysign)|[copysignf –](#copysignf)|[Cos](#cos)|  
|[cosf](#cosf)|[COSH](#cosh)|[coshf](#coshf)|  
|[cospi](#cospi)|[cospif –](#cospif)|[erf](#erf)|  
|[erfc](#erfc)|[erfcf](#erfcf)|[erfcinv –](#erfcinv)|  
|[erfcinvf](#erfcinvf)|[erff](#erff)|[erfinv –](#erfinv)|  
|[erfinvf –](#erfinvf)|[exp](#exp)|[exp10](#exp10)|  
|[exp10f –](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|  
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|  
|[fabs](#fabs)|[fabsf –](#fabsf)|[Floor](#floor)| 
|[fdim –](#fdim)|[fdimf –](#fdimf)|| 
|[floorf](#floorf)|[fma](#fma)|[fmaf –](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)|| 
|[Fmin](#fmin)|[fminf –](#fminf)|[fmod](#fmod)|  
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|  
|[frexpf](#frexpf)|[hypot –](#hypot)|[hypotf –](#hypotf)|  
|[ilogb –](#ilogb)|[ilogbf](#ilogbf)|[isfinite](#isfinite)|  
|[isinf –](#isinf)|[isNaN](#isnan)|[isnormal –](#isnormal)|  
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[lgamma](#lgamma)|  
|[lgammaf](#lgammaf)|[Protokolu](#log)|[log10](#log10)|  
|[log10f](#log10f)|[log1p –](#log1p)|[log1pf](#log1pf)|  
|[log2](#log2)|[log2f](#log2f)|[logb –](#logb)|  
|[logbf –](#logbf)|[logf –](#logf)|[modf –](#modf)|  
|[modff](#modff)|[NaN.](#nan)|[nanf –](#nanf)|  
|[nearbyint –](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter –](#nextafter)|  
|[nextafterf](#nextafterf)|[Phi –](#phi)|[phif –](#phif)|  
|[Pow](#pow)|[powf –](#powf)|[probit –](#probit)|  
|[probitf](#probitf)|[rcbrt](#rcbrt)|[rcbrtf](#rcbrtf)|  
|[Zbývající](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|  
|[remquof](#remquof)|[Zaokrouhlit](#round)|[roundf –](#roundf)|  
|[rsqrt –](#rsqrt)|[rsqrtf](#rsqrtf)|[scalb –](#scalb)|  
|[scalbf](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|  
|[signbit –](#signbit)|[signbitf –](#signbitf)|[Sin](#sin)|  
|[sincos –](#sincos)|[sincosf](#sincosf)|[sinf –](#sinf)|  
|[SINH](#sinh)|[sinhf](#sinhf)|[sinpi –](#sinpi)|  
|[sinpif –](#sinpif)|[sqrt](#sqrt)|[sqrtf](#sqrtf)|  
|[Tan](#tan)|[tanf –](#tanf)|[TANH](#tanh)|  
|[tanhf](#tanhf)|[tanpi –](#tanpi)|[tanpif –](#tanpif)|  
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[TRUNC](#trunc)|  
|[truncf –](#truncf)|  
  
##  <a name="acos"></a>  ACOS  
 Vypočítá Arkus kosinus argument  
  
```  
inline float acos(float _X) restrict(amp);

 
inline double acos(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí Arkus kosinus hodnotu argumentu  
  
##  <a name="acosf"></a>  acosf –  
 Vypočítá Arkus kosinus argument  
  
```  
inline float acosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí Arkus kosinus hodnotu argumentu  
  
##  <a name="acosh"></a>  acosh –  
 Vypočítá inverzní hyperbolický kosinus argumentu  
  
```  
inline float acosh(float _X) restrict(amp);

 
inline double acosh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní hyperbolický kosinus hodnotu argumentu  
  
##  <a name="acoshf"></a>  acoshf –  
 Vypočítá inverzní hyperbolický kosinus argumentu  
  
```  
inline float acoshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní hyperbolický kosinus hodnotu argumentu  
  
##  <a name="asin"></a>  ASIN  
 Vypočítá Arkus sinus argument  
  
```  
inline float asin(float _X) restrict(amp);

 
inline double asin(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí Arkus sinus hodnotu argumentu  
  
##  <a name="asinf"></a>  asinf –  
 Vypočítá Arkus sinus argument  
  
```  
inline float asinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí Arkus sinus hodnotu argumentu  
  
##  <a name="asinh"></a>  asinh –  
 Vypočítá inverzní hyperbolický sinus argumentu  
  
```  
inline float asinh(float _X) restrict(amp);

 
inline double asinh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní hyperbolický sinus hodnotu argumentu  
  
##  <a name="asinhf"></a>  asinhf –  
 Vypočítá inverzní hyperbolický sinus argumentu  
  
```  
inline float asinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní hyperbolický sinus hodnotu argumentu  
  
##  <a name="atan"></a>  Atan  
 Vypočítá Arkus tangens argument  
  
```  
inline float atan(float _X) restrict(amp);

 
inline double atan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí Arkus hodnotu argumentu  
  
##  <a name="atan2"></a>  ATAN2  
 Vypočítá Arkus tangens _Y/_X  
  
```  
inline float atan2(
    float _Y,  
    float _X) restrict(amp);

 
inline double atan2(
    double _Y,  
    double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu Arkus _Y/_X  
  
##  <a name="atan2f"></a>  atan2f –  
 Vypočítá Arkus tangens _Y/_X  
  
```  
inline float atan2f(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu Arkus _Y/_X  
  
##  <a name="atanf"></a>  atanf –  
 Vypočítá Arkus tangens argument  
  
```  
inline float atanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí Arkus hodnotu argumentu  
  
##  <a name="atanh"></a>  atanh –  
 Vypočítá inverzní hyperbolický tangens argumentu  
  
```  
inline float atanh(float _X) restrict(amp);

 
inline double atanh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní hyperbolický tangens hodnota argumentu  
  
##  <a name="atanhf"></a>  atanhf –  
 Vypočítá inverzní hyperbolický tangens argumentu  
  
```  
inline float atanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní hyperbolický tangens hodnota argumentu  
  
##  <a name="cbrt"></a>  cbrt –  
 Vypočítá skutečné kořenové datové krychle argumentu  
  
```  
inline float cbrt(float _X) restrict(amp);

 
inline double cbrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí skutečné kořenové datové krychle argumentu  
  
##  <a name="cbrtf"></a>  cbrtf –  
 Vypočítá skutečné kořenové datové krychle argumentu  
  
```  
inline float cbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí skutečné kořenové datové krychle argumentu  
  
##  <a name="ceil"></a>  ceil  
 Vypočítá se mezní hodnota argumentu  
  
```  
inline float ceil(float _X) restrict(amp);

 
inline double ceil(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí se mezní hodnota argumentu  
  
##  <a name="ceilf"></a>  ceilf –  
 Vypočítá se mezní hodnota argumentu  
  
```  
inline float ceilf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí se mezní hodnota argumentu  
  
##  <a name="copysign"></a>  copysign –  
 Vytvoří hodnotu s odhad _X a znaménko _Y  
  
```  
inline float copysign(
    float _X,  
    float _Y) restrict(amp);

 
inline double copysign(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu s odhad _X a znaménko _Y  
  
##  <a name="copysignf"></a>  copysignf –  
 Vytvoří hodnotu s odhad _X a znaménko _Y  
  
```  
inline float copysignf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu s odhad _X a znaménko _Y  
  
##  <a name="cos"></a>  Cos  
 Výpočet kosinu argument  
  
```  
inline float cos(float _X) restrict(amp);

 
inline double cos(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kosinus hodnotu argumentu  
  
##  <a name="cosf"></a>  cosf –  
 Výpočet kosinu argument  
  
```  
inline float cosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kosinus hodnotu argumentu  
  
##  <a name="cosh"></a>  COSH  
 Vypočítá hodnotu hyperbolický kosinus argumentu  
  
```  
inline float cosh(float _X) restrict(amp);

 
inline double cosh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hyperbolický kosinus hodnotu argumentu  
  
##  <a name="coshf"></a>  coshf –  
 Vypočítá hodnotu hyperbolický kosinus argumentu  
  
```  
inline float coshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hyperbolický kosinus hodnotu argumentu  
  
##  <a name="cospi"></a>  cospi –  
 Vypočítá kosinus hodnotu čísla pí * _X  
  
```  
inline float cospi(float _X) restrict(amp);

 
inline double cospi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kosinus hodnotu čísla pí * _X  
  
##  <a name="cospif"></a>  cospif –  
 Vypočítá kosinus hodnotu čísla pí * _X  
  
```  
inline float cospif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kosinus hodnotu čísla pí * _X  
  
##  <a name="erf"></a>  ERF –  
 Vypočítá Chyba funkce _X  
  
```  
inline float erf(float _X) restrict(amp);

 
inline double erf(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí Chyba funkce _X  
  
##  <a name="erfc"></a>  ERFC –  
 Vypočítá doplňkové Chyba funkce _X  
  
```  
inline float erfc(float _X) restrict(amp);

 
inline double erfc(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí doplňkovou chybovou funkci _X  
  
##  <a name="erfcf"></a>  erfcf –  
 Vypočítá doplňkové Chyba funkce _X  
  
```  
inline float erfcf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí doplňkovou chybovou funkci _X  
  
##  <a name="erfcinv"></a>  erfcinv –  
 Vypočítá inverzní doplňkové Chyba funkce _X  
  
```  
inline float erfcinv(float _X) restrict(amp);

 
inline double erfcinv(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní doplňkové Chyba funkce _X  
  
##  <a name="erfcinvf"></a>  erfcinvf –  
 Vypočítá inverzní doplňkové Chyba funkce _X  
  
```  
inline float erfcinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní doplňkové Chyba funkce _X  
  
##  <a name="erff"></a>  erff –  
 Vypočítá Chyba funkce _X  
  
```  
inline float erff(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí Chyba funkce _X  
  
##  <a name="erfinv"></a>  erfinv –  
 Vypočítá inverzní Chyba funkce _X  
  
```  
inline float erfinv(float _X) restrict(amp);

 
inline double erfinv(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní Chyba funkce _X  
  
##  <a name="erfinvf"></a>  erfinvf –  
 Vypočítá inverzní Chyba funkce _X  
  
```  
inline float erfinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní Chyba funkce _X  
  
##  <a name="exp10"></a>  exp10 –  
 Vypočítá exponenciální argumentu základních-10  
  
```  
inline float exp10(float _X) restrict(amp);

 
inline double exp10(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu exponenciálního argumentu základu 10  
  
##  <a name="exp10f"></a>  exp10f –  
 Vypočítá exponenciální argumentu základních-10  
  
```  
inline float exp10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu exponenciálního argumentu základu 10  
  
##  <a name="expm1"></a>  expm1 –  
 Vypočítá exponenciální funkci argumentu o základu e a odečte 1.  
  
```  
inline float expm1(float exponent) restrict(amp);

 
inline double expm1(double exponent) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `exponent`  
 Exponenciální termín *n* matematickém výrazu `e` <sup>n</sup>, kde `e` je základ přirozeného logaritmu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu exponenciální funkce argumentu o základu e a odečte 1.  
  
##  <a name="expm1f"></a>  expm1f –  
 Vypočítá exponenciální funkci argumentu o základu e a odečte 1.  
  
```  
inline float expm1f(float exponent) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `exponent`  
 Exponenciální termín *n* matematickém výrazu `e` <sup>n</sup>, kde `e` je základ přirozeného logaritmu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu exponenciální funkce argumentu o základu e a odečte 1.  
  
##  <a name="exp"></a>  Exp  
 Vypočítá exponenciální argumentu základní e  
  
```  
inline float exp(float _X) restrict(amp);

 
inline double exp(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu exponenciálního argumentu základem e  
  
##  <a name="expf"></a>  expf –  
 Vypočítá exponenciální argumentu základní e  
  
```  
inline float expf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu exponenciálního argumentu základem e  
  
##  <a name="exp2"></a>  exp2 –  
 Vypočítá exponenciální argumentu základní-2  
  
```  
inline float exp2(float _X) restrict(amp);

 
inline double exp2(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu exponenciálního argumentu 2 základní  
  
##  <a name="exp2f"></a>  exp2f –  
 Vypočítá exponenciální argumentu základní-2  
  
```  
inline float exp2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu exponenciálního argumentu 2 základní  
  
##  <a name="fabs"></a>  fabs  
 Vrátí absolutní hodnotu argumentu  
  
```  
inline float fabs(float _X) restrict(amp);

 
inline double fabs(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí absolutní hodnotu argumentu  
  
##  <a name="fabsf"></a>  fabsf –  
 Vrátí absolutní hodnotu argumentu  
  
```  
inline float fabsf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí absolutní hodnotu argumentu  

## <a name="fdim"></a> fdim –  
Vypočítá kladné rozdíl mezi argumenty.
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
`_X` Hodnota s plovoucí desetinnou čárkou `_Y` s plovoucí desetinnou čárkou


### <a name="return-value"></a>Návratová hodnota
Rozdíl mezi _X a _Y Pokud _X je větší než _Y; jinak, + 0.
 
## <a name="fdimf"></a> fdimf –  
Vypočítá kladné rozdíl mezi argumenty.
```
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```
### <a name="parameters"></a>Parametry
`_X` Hodnota s plovoucí desetinnou čárkou `_Y` s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota
Rozdíl mezi _X a _Y Pokud _X je větší než _Y; jinak, + 0. 
  
##  <a name="floor"></a>  Floor  
 Vypočítá podlaží argumentu  
  
```  
inline float floor(float _X) restrict(amp);

 
inline double floor(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí podlaží argumentu  
  
##  <a name="floorf"></a>  floorf –  
 Vypočítá podlaží argumentu  
  
```  
inline float floorf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí podlaží argumentu  

## <a name="a-namefma-fma"></a><a name="fma"> FMA –  
Vypočítá produktu jsou zadané argumenty první a druhý, pak přidá třetí argument zadaný na výsledek; celý výpočet se provádí jako jednu operaci.
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
`_X` První argument s plovoucí desetinnou čárkou.
`_Y` Druhý argument s plovoucí desetinnou čárkou.
`_Z` Třetí argument s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota
Výsledkem výrazu (_X * _Y) + _Z –. Celý výpočet se provádí jako jednu operaci; To znamená, dílčí výrazy jsou vypočítávány k nekonečné přesnost a konečný výsledek zaokrouhlen. 

## <a name="fmaf"></a> fmaf –  
Vypočítá produktu jsou zadané argumenty první a druhý, pak přidá třetí argument zadaný na výsledek; celý výpočet se provádí jako jednu operaci.
```
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```  
### <a name="parameters"></a>Parametry
`_X` První argument s plovoucí desetinnou čárkou.
`_Y` Druhý argument s plovoucí desetinnou čárkou.
`_Z` Třetí argument s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota
Výsledkem výrazu (_X * _Y) + _Z –. Celý výpočet se provádí jako jednu operaci; To znamená, dílčí výrazy jsou vypočítávány k nekonečné přesnost a konečný výsledek zaokrouhlen.
  
##  <a name="fmax"></a>  Fmax  
 Určit maximální číselná hodnota, která jsou argumenty  
  
```  
inline float fmax(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmax(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí maximální hodnotu číselného argumenty  
  
##  <a name="fmaxf"></a>  fmaxf –  
 Určit maximální číselná hodnota, která jsou argumenty  
  
```  
inline float fmaxf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí maximální hodnotu číselného argumenty  
  
##  <a name="fmin"></a>  Fmin  
 Určení minimální číselná hodnota z argumentů  
  
```  
inline float fmin(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmin(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí minimální hodnotu číselného argumenty  
  
##  <a name="fminf"></a>  fminf –  
 Určení minimální číselná hodnota z argumentů  
  
```  
inline float fminf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí minimální hodnotu číselného argumenty  
  
##  <a name="fmod"></a>  fmod – funkce (C++ AMP)  
 Vypočítá zbytek první zadaného argumentu dělený druhý zadaného argumentu.  
  
```  
inline float fmod(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmod(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 První argument s plovoucí desetinnou čárkou.  
  
 `_Y`  
 Druhý argument s plovoucí desetinnou čárkou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Zbývající část `_X` dělený `_Y`; to znamená, hodnota `_X`  -  `_Y` *n*, kde *n* je celé číslo typu integer tak, aby odhad `_X`  -  `_Y` *n* je menší než odhad `_Y`.  
  
##  <a name="fmodf"></a>  fmodf –  
 Vypočítá zbytek první zadaného argumentu dělený druhý zadaného argumentu.  
  
```  
inline float fmodf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 První argument s plovoucí desetinnou čárkou.  
  
 `_Y`  
 Druhý argument s plovoucí desetinnou čárkou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Zbývající část `_X` dělený `_Y`; to znamená, hodnota `_X`  -  `_Y` *n*, kde *n* je celé číslo typu integer tak, aby odhad `_X`  -  `_Y` *n* je menší než odhad `_Y`.  
  
##  <a name="fpclassify"></a>  fpclassify –  
 Klasifikuje hodnota argumentu jako nula NaN, nekonečné, normální subnormal,  
  
```  
inline int fpclassify(float _X) restrict(amp);

 
inline int fpclassify(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu čísla makra klasifikace odpovídající hodnotě argumentu.  
  
##  <a name="frexp"></a>  frexp –  
 Získá mantisa a exponent _X  
  
```  
inline float frexp(
    float _X,  
    _Out_ int* _Exp) restrict(amp);

 
inline double frexp(
    double _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Exp`  
 Vrátí exponent _X celé číslo s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X mantisa  
  
##  <a name="frexpf"></a>  frexpf –  
 Získá mantisa a exponent _X  
  
```  
inline float frexpf(
    float _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Exp`  
 Vrátí exponent _X celé číslo s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X mantisa  
  
##  <a name="hypot"></a>  hypot –  
 Vypočítá druhou odmocninu čísla součet kvadratických _X a _Y  
  
```  
inline float hypot(
    float _X,  
    float _Y) restrict(amp);

 
inline double hypot(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí druhou odmocninu čísla součet kvadratických _X a _Y  
  
##  <a name="hypotf"></a>  hypotf –  
 Vypočítá druhou odmocninu čísla součet kvadratických _X a _Y  
  
```  
inline float hypotf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí druhou odmocninu čísla součet kvadratických _X a _Y  
  
##  <a name="ilogb"></a>  ilogb –  
 Extrahování exponent _X jako hodnotu podepsaný int  
  
```  
inline int ilogb(float _X) restrict(amp);

 
inline int ilogb(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí exponent _X jako hodnotu podepsaný int  
  
##  <a name="ilogbf"></a>  ilogbf –  
 Extrahování exponent _X jako hodnotu podepsaný int  
  
```  
inline int ilogbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí exponent _X jako hodnotu podepsaný int  
  
##  <a name="isfinite"></a>  isfinite  
 Určuje, zda argument má hodnotu konečné  
  
```  
inline int isfinite(float _X) restrict(amp);

 
inline int isfinite(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nenulovou hodnotu, pokud argument má hodnotu konečné  
  
##  <a name="isinf"></a>  isinf –  
 Určuje, zda je argument nekonečna  
  
```  
inline int isinf(float _X) restrict(amp);

 
inline int isinf(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nenulovou hodnotu, pokud má argument nekonečné hodnotu  
  
##  <a name="isnan"></a>  isNaN  
 Určuje, zda je argument NaN.  
  
```  
inline int isnan(float _X) restrict(amp);

 
inline int isnan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nenulovou hodnotu, pokud argument má hodnotu NaN.  
  
##  <a name="isnormal"></a>  isnormal –  
 Určuje, zda je argument normální  
  
```  
inline int isnormal(float _X) restrict(amp);

 
inline int isnormal(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nenulovou hodnotu, pokud má argument normální hodnotu  
  
##  <a name="ldexp"></a>  ldexp –  
 Vypočítá reálné číslo ze zadaného mantisa a exponent.  
  
```  
inline float ldexp(
    float _X,  
    int _Exp) restrict(amp);

 
inline double ldexp(
    double _X,  
    double _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou, mantisa  
  
 `_Exp`  
 Celočíselná hodnota, exponentu  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X * 2 ^ _Exp  
  
##  <a name="ldexpf"></a>  ldexpf –  
 Vypočítá reálné číslo ze zadaného mantisa a exponent.  
  
```  
inline float ldexpf(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou, mantisa  
  
 `_Exp`  
 Celočíselná hodnota, exponentu  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X * 2 ^ _Exp  
  
##  <a name="lgamma"></a>  lgamma –  
 Vypočítá přirozený logaritmus absolutní hodnotu gama argumentu  
  
```  
inline float lgamma(
    float _X,  
    _Out_ int* _Sign) restrict(amp);

 
inline double lgamma(
    double _X,  
    _Out_ int* _Sign) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Sign`  
 Vrátí znaménko  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí přirozený logaritmus absolutní hodnotu gama argumentu  
  
##  <a name="lgammaf"></a>  lgammaf –  
 Vypočítá přirozený logaritmus absolutní hodnotu gama argumentu  
  
```  
inline float lgammaf(
    float _X,  
    _Out_ int* _Sign) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Sign`  
 Vrátí znaménko  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí přirozený logaritmus absolutní hodnotu gama argumentu  
  
##  <a name="log"></a>  Protokolu  
 Vypočítá základní e logaritmus argumentu  
  
```  
inline float log(float _X) restrict(amp);

 
inline double log(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí logaritmus základem e argumentu  
  
##  <a name="log10"></a>  LOG10  
 Vypočítá logaritmus o základu 10 argument  
  
```  
inline float log10(float _X) restrict(amp);

 
inline double log10(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí logaritmus o základu 10 argument  
  
##  <a name="log10f"></a>  log10f –  
 Vypočítá logaritmus o základu 10 argument  
  
```  
inline float log10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí logaritmus o základu 10 argument  
  
##  <a name="log1p"></a>  log1p –  
 Vypočítá základní e logaritmus 1 plus argument  
  
```  
inline float log1p(float _X) restrict(amp);

 
inline double log1p(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí logaritmus základem e 1 plus argument  
  
##  <a name="log1pf"></a>  log1pf –  
 Vypočítá základní e logaritmus 1 plus argument  
  
```  
inline float log1pf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí logaritmus základem e 1 plus argument  
  
##  <a name="log2"></a>  log2  
 Vypočítá logaritmus o základu 2 argumentu  
  
```  
inline float log2(float _X) restrict(amp);

 
inline double log2(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí logaritmus o základu 10 argument  
  
##  <a name="log2f"></a>  log2f –  
 Vypočítá logaritmus o základu 2 argumentu  
  
```  
inline float log2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí logaritmus o základu 10 argument  
  
##  <a name="logb"></a>  logb –  
 Extrahuje exponent _X, jako číslo se znaménkem hodnoty ve formátu s plovoucí desetinnou čárkou  
  
```  
inline float logb(float _X) restrict(amp);

 
inline double logb(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí exponent podepsaný _X  
  
##  <a name="logbf"></a>  logbf –  
 Extrahuje exponent _X, jako číslo se znaménkem hodnoty ve formátu s plovoucí desetinnou čárkou  
  
```  
inline float logbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí exponent podepsaný _X  
  
##  <a name="logf"></a>  logf –  
 Vypočítá základní e logaritmus argumentu  
  
```  
inline float logf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí logaritmus základem e argumentu  
  
##  <a name="modf"></a>  modf –  
 Rozdělí zadaný argument do zlomkové a částí celé číslo.  
  
```  
inline float modf(
    float _X,  
    _Out_ float* _Iptr) restrict(amp);

 
inline double modf(
    double _X,  
    _Out_ double* _Iptr) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Iptr` (out parametr)  
 Celočíselnou část `_X`, jako hodnotu s plovoucí desetinnou čárkou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Podepsaný zlomkové části `_X`.  
  
##  <a name="modff"></a>  modff –  
 Rozdělí zadaný argument do zlomkové a částí celé číslo.  
  
```  
inline float modff(
    float _X,  
    _Out_ float* _Iptr) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Iptr`  
 Celočíselnou část `_X`, jako hodnotu s plovoucí desetinnou čárkou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí podepsaný zlomkové části `_X`.  
  
##  <a name="nan"></a>  NaN.  
 Vrátí quiet NaN  
  
```  
inline double nan(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí quiet NaN, pokud se obsah k dispozici v _X  
  
##  <a name="nanf"></a>  nanf –  
 Vrátí quiet NaN  
  
```  
inline float nanf(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí quiet NaN, pokud se obsah k dispozici v _X  
  
##  <a name="nearbyint"></a>  nearbyint –  
 Zaokrouhlí argument na celočíselnou hodnotu ve formátu s plovoucí desetinnou čárkou, pomocí aktuální směr zaokrouhlení.  
  
```  
inline float nearbyint(float _X) restrict(amp);

 
inline double nearbyint(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí zaokrouhlené celočíselnou hodnotu.  
  
##  <a name="nearbyintf"></a>  nearbyintf –  
 Zaokrouhlí argument na celočíselnou hodnotu ve formátu s plovoucí desetinnou čárkou, pomocí aktuální směr zaokrouhlení.  
  
```  
inline float nearbyintf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí zaokrouhlené celočíselnou hodnotu.  
  
##  <a name="nextafter"></a>  nextafter –  
 Zjistit další reprezentovat hodnotu, v typu funkce, po _X ve směru _Y  
  
```  
inline float nextafter(
    float _X,  
    float _Y) restrict(amp);

 
inline double nextafter(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu dalšího reprezentovat v typu funkce, po _X ve směru _Y  
  
##  <a name="nextafterf"></a>  nextafterf –  
 Zjistit další reprezentovat hodnotu, v typu funkce, po _X ve směru _Y  
  
```  
inline float nextafterf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu dalšího reprezentovat v typu funkce, po _X ve směru _Y  
  
##  <a name="phi"></a>  Phi –  
 Vrátí kumulativní distribuční funkci argumentu  
  
```  
inline float phi(float _X) restrict(amp);

 
inline double phi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kumulativní distribuční funkci argumentu  
  
##  <a name="phif"></a>  phif –  
 Vrátí kumulativní distribuční funkci argumentu  
  
```  
inline float phif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kumulativní distribuční funkci argumentu  
  
##  <a name="pow"></a>  Pow  
 Vypočítá _X mocninu _Y  
  
```  
inline float pow(
    float _X,  
    float _Y) restrict(amp);

 
inline double pow(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou, základní  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou, exponentu  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="powf"></a>  powf –  
 Vypočítá _X mocninu _Y  
  
```  
inline float powf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou, základní  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou, exponentu  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="probit"></a>  probit –  
 Vrátí inverzní kumulativní distribuční funkci argumentu  
  
```  
inline float probit(float _X) restrict(amp);

 
inline double probit(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní kumulativní distribuční funkci argumentu  
  
##  <a name="probitf"></a>  probitf –  
 Vrátí inverzní kumulativní distribuční funkci argumentu  
  
```  
inline float probitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí inverzní kumulativní distribuční funkci argumentu  
  
##  <a name="rcbrt"></a>  rcbrt –  
 Vrátí vzájemné kořenové datové krychle argumentu  
  
```  
inline float rcbrt(float _X) restrict(amp);

 
inline double rcbrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí vzájemné kořenové datové krychle argumentu  
  
##  <a name="rcbrtf"></a>  rcbrtf –  
 Vrátí vzájemné kořenové datové krychle argumentu  
  
```  
inline float rcbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí vzájemné kořenové datové krychle argumentu  
  
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
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X REM _Y  
  
##  <a name="remainderf"></a>  remainderf –  
 Vypočítá zbytek: _X REM _Y  
  
```  
inline float remainderf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X REM _Y  
  
##  <a name="remquo"></a>  remquo –  
 Vypočítá zbytek první zadaného argumentu dělený druhý zadaného argumentu. Také vypočítá podíl mantisy první zadaného argumentu dělený mantisy druhý zadaného argumentu a vrátí podílu pomocí umístění, ve třetím argumentu.  
  
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
 `_X`  
 První argument s plovoucí desetinnou čárkou.  
  
 `_Y`  
 Druhý argument s plovoucí desetinnou čárkou.  
  
 `_Quo` (out parametr)  
 Adresa celé číslo, které se používá k vrácení podíl zlomkové bity `_X` dělený zlomkové bity `_Y`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí zbytek `_X` dělený `_Y`.  
  
##  <a name="remquof"></a>  remquof –  
 Vypočítá zbytek první zadaného argumentu dělený druhý zadaného argumentu. Také vypočítá podíl mantisy první zadaného argumentu dělený mantisy druhý zadaného argumentu a vrátí podílu pomocí umístění, ve třetím argumentu.  
  
```  
inline float remquof(
    float _X,  
    float _Y,  
    _Out_ int* _Quo) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 První argument s plovoucí desetinnou čárkou.  
  
 `_Y`  
 Druhý argument s plovoucí desetinnou čárkou.  
  
 `_Quo` (out parametr)  
 Adresa celé číslo, které se používá k vrácení podíl zlomkové bity `_X` dělený zlomkové bity `_Y`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí zbytek `_X` dělený `_Y`.  
  
##  <a name="round"></a>  Zaokrouhlit  
 Zaokrouhlí _X na nejbližší celé číslo  
  
```  
inline float round(float _X) restrict(amp);

 
inline double round(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí na nejbližší celé číslo _X  
  
##  <a name="roundf"></a>  roundf –  
 Zaokrouhlí _X na nejbližší celé číslo  
  
```  
inline float roundf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí na nejbližší celé číslo _X  
  
##  <a name="rsqrt"></a>  rsqrt –  
 Vrátí vzájemné druhé odmocniny argumentu  
  
```  
inline float rsqrt(float _X) restrict(amp);

 
inline double rsqrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí vzájemné druhé odmocniny argumentu  
  
##  <a name="rsqrtf"></a>  rsqrtf –  
 Vrátí vzájemné druhé odmocniny argumentu  
  
```  
inline float rsqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí vzájemné druhé odmocniny argumentu  
  
##  <a name="scalb"></a>  scalb –  
 Vynásobí _X podle flt_radix – k _Y napájení  
  
```  
inline float scalb(
    float _X,  
    float _Y) restrict(amp);

 
inline double scalb(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X * (flt_radix – ^ _Y)  
  
##  <a name="scalbf"></a>  scalbf –  
 Vynásobí _X podle flt_radix – k _Y napájení  
  
```  
inline float scalbf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X * (flt_radix – ^ _Y)  
  
##  <a name="scalbn"></a>  scalbn –  
 Vynásobí _X podle flt_radix – k _Y napájení  
  
```  
inline float scalbn(
    float _X,  
    int _Y) restrict(amp);

 
inline double scalbn(
    double _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X * (flt_radix – ^ _Y)  
  
##  <a name="scalbnf"></a>  scalbnf –  
 Vynásobí _X podle flt_radix – k _Y napájení  
  
```  
inline float scalbnf(
    float _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X * (flt_radix – ^ _Y)  
  
##  <a name="signbit"></a>  signbit –  
 Určuje, zda je záporné znaménko _X  
  
```  
inline int signbit(float _X) restrict(amp);

 
inline int signbit(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nenulovou hodnotu, pokud znaménko _X je záporná.  
  
##  <a name="signbitf"></a>  signbitf –  
 Určuje, zda je záporné znaménko _X  
  
```  
inline int signbitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nenulovou hodnotu, pokud znaménko _X je záporná.  
  
##  <a name="sin"></a>  Sin  
 Vypočítá hodnotu sinus argumentu  
  
```  
inline float sin(float _X) restrict(amp);

 
inline double sin(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí sinus hodnotu argumentu  
  
##  <a name="sinf"></a>  sinf –  
 Vypočítá hodnotu sinus argumentu  
  
```  
inline float sinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí sinus hodnotu argumentu  
  
##  <a name="sincos"></a>  sincos –  
 Vypočítá sinus a kosinus hodnotu _X  
  
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
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_S`  
 Vrátí sinus hodnotu _X  
  
 `_C`  
 Vrátí kosinus hodnotu _X  
  
##  <a name="sincosf"></a>  sincosf –  
 Vypočítá sinus a kosinus hodnotu _X  
  
```  
inline void sincosf(
    float _X,  
    _Out_ float* _S,  
    _Out_ float* _C) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_S`  
 Vrátí sinus hodnotu _X  
  
 `_C`  
 Vrátí kosinus hodnotu _X  
  
##  <a name="sinh"></a>  SINH  
 Vypočítá hodnotu hyperbolický sinus argumentu  
  
```  
inline float sinh(float _X) restrict(amp);

 
inline double sinh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hyperbolický sinus hodnotu argumentu  
  
##  <a name="sinhf"></a>  sinhf –  
 Vypočítá hodnotu hyperbolický sinus argumentu  
  
```  
inline float sinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hyperbolický sinus hodnotu argumentu  
  
##  <a name="sinpi"></a>  sinpi –  
 Vypočítá sinus hodnotu čísla pí * _X  
  
```  
inline float sinpi(float _X) restrict(amp);

 
inline double sinpi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí sinus hodnotu čísla pí * _X  
  
##  <a name="sinpif"></a>  sinpif –  
 Vypočítá sinus hodnotu čísla pí * _X  
  
```  
inline float sinpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí sinus hodnotu čísla pí * _X  
  
##  <a name="sqrt"></a>  Sqrt  
 Vypočítá kořenu squre argumentu  
  
```  
inline float sqrt(float _X) restrict(amp);

 
inline double sqrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kořenu squre argumentu  
  
##  <a name="sqrtf"></a>  sqrtf –  
 Vypočítá kořenu squre argumentu  
  
```  
inline float sqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kořenu squre argumentu  
  
##  <a name="tan"></a>  Tan  
 Vypočítá tečný hodnotu argumentu  
  
```  
inline float tan(float _X) restrict(amp);

 
inline double tan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí tangens hodnotu argumentu  
  
##  <a name="tanf"></a>  tanf –  
 Vypočítá tečný hodnotu argumentu  
  
```  
inline float tanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí tangens hodnotu argumentu  
  
##  <a name="tanh"></a>  TANH  
 Vypočítá hyperbolický tangens hodnotu argumentu  
  
```  
inline float tanh(float _X) restrict(amp);

 
inline double tanh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hyperbolický tangens hodnotu argumentu  
  
##  <a name="tanhf"></a>  tanhf –  
 Vypočítá hyperbolický tangens hodnotu argumentu  
  
```  
inline float tanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hyperbolický tangens hodnotu argumentu  
  
##  <a name="tanpi"></a>  tanpi –  
 Vypočítá tečný hodnotu čísla pí * _X  
  
```  
inline float tanpi(float _X) restrict(amp);

 
inline double tanpi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí tangens hodnotu čísla pí * _X  
  
##  <a name="tanpif"></a>  tanpif –  
 Vypočítá tečný hodnotu čísla pí * _X  
  
```  
inline float tanpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí tangens hodnotu čísla pí * _X  
  
##  <a name="tgamma"></a>  tgamma –  
 Vypočítá gama funkce _X  
  
```  
inline float tgamma(float _X) restrict(amp);

 
inline double tgamma(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek gama funkce _X  
  
##  <a name="tgammaf"></a>  tgammaf –  
 Vypočítá gama funkce _X  
  
```  
inline float tgammaf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek gama funkce _X  
  
##  <a name="trunc"></a>  TRUNC  
 Zkrátí argument pro komponentu celé číslo  
  
```  
inline float trunc(float _X) restrict(amp);

 
inline double trunc(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí komponentu celé číslo argumentu  
  
##  <a name="truncf"></a>  truncf –  
 Zkrátí argument pro komponentu celé číslo  
  
```  
inline float truncf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí komponentu celé číslo argumentu  
  
## <a name="see-also"></a>Viz také  
 [Concurrency::precise_math – obor názvů](concurrency-precise-math-namespace.md)
