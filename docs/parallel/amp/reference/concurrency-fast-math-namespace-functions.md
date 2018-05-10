---
title: Concurrency::fast_math – obor názvů funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9bd20e2e1d88564c7e688e1e0c9c2392f1f4f2ac
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="concurrencyfastmath-namespace-functions"></a>Funkce Concurrency::fast_math – obor názvů
||||  
|-|-|-|  
|[ACOS](#acos)|[acosf](#acosf)|[ASIN](#asin)|  
|[asinf –](#asinf)|[Atan](#atan)|[atan2](#atan2)|  
|[atan2f](#atan2f)|[atanf –](#atanf)|[ceil](#ceil)|  
|[ceilf –](#ceilf)|[Cos](#cos)|[cosf](#cosf)|  
|[COSH](#cosh)|[coshf](#coshf)|[exp](#exp)|  
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|  
|[fabs](#fabs)|[fabsf –](#fabsf)|[Floor](#floor)|  
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|  
|[Fmin](#fmin)|[fminf –](#fminf)|[fmod](#fmod)|  
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf](#frexpf)|  
|[isfinite](#isfinite)|[isinf –](#isinf)|[isNaN](#isnan)|  
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[Protokolu](#log)|  
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|  
|[log2f](#log2f)|[logf –](#logf)|[modf –](#modf)|  
|[modff](#modff)|[Pow](#pow)|[powf –](#powf)|  
|[Zaokrouhlit](#round)|[roundf –](#roundf)|[rsqrt –](#rsqrt)|  
|[rsqrtf](#rsqrtf)|[signbit –](#signbit)|[signbitf –](#signbitf)|  
|[Sin](#sin)|[sincos –](#sincos)|[sincosf](#sincosf)|  
|[sinf –](#sinf)|[SINH](#sinh)|[sinhf](#sinhf)|  
|[sqrt](#sqrt)|[sqrtf](#sqrtf)|[Tan](#tan)|  
|[tanf –](#tanf)|[TANH](#tanh)|[tanhf](#tanhf)|  
|[TRUNC](#trunc)|[truncf –](#truncf)|  
  
##  <a name="acos"></a>  ACOS  
 Vypočítá Arkus kosinus argument  
  
```  
inline float acos(float _X) restrict(amp);
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
  
##  <a name="asin"></a>  ASIN  
 Vypočítá Arkus sinus argument  
  
```  
inline float asin(float _X) restrict(amp);
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
  
##  <a name="atan"></a>  Atan  
 Vypočítá Arkus tangens argument  
  
```  
inline float atan(float _X) restrict(amp);
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
  
##  <a name="ceil"></a>  ceil  
 Vypočítá se mezní hodnota argumentu  
  
```  
inline float ceil(float _X) restrict(amp);
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
  
##  <a name="cos"></a>  Cos  
 Výpočet kosinu argument  
  
```  
inline float cos(float _X) restrict(amp);
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
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hyperbolický kosinus hodnotu argumentu  
  
##  <a name="exp"></a>  Exp  
 Vypočítá exponenciální argumentu základní e  
  
```  
inline float exp(float _X) restrict(amp);
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
  
##  <a name="fabs"></a>  fabs  
 Vrátí absolutní hodnotu argumentu  
  
```  
inline float fabs(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
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
  
##  <a name="floor"></a>  Floor  
 Vypočítá podlaží argumentu  
  
```  
inline float floor(float _X) restrict(amp);
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
  
##  <a name="fmax"></a>  Fmax  
 Určit maximální číselná hodnota, která jsou argumenty  
  
```  
inline float max(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
 `_Y`  
 Celočíselná hodnota  
  
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
inline float min(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
 `_Y`  
 Celočíselná hodnota  
  
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
  
##  <a name="fmod"></a>  fmod  
 Vypočítá zbytek _X/_Y s plovoucí desetinnou čárkou  
  
```  
inline float fmod(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí zbytek _X/_Y s plovoucí desetinnou čárkou  
  
##  <a name="fmodf"></a>  fmodf –  
 Vypočítá zbytek _X/_Y s plovoucí desetinnou čárkou.  
  
```  
inline float fmodf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí zbytek _X/_Y s plovoucí desetinnou čárkou  
  
##  <a name="frexp"></a>  frexp –  
 Získá mantisa a exponent _X  
  
```  
inline float frexp(
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
  
##  <a name="isfinite"></a>  isfinite  
 Určuje, zda argument má hodnotu konečné  
  
```  
inline int isfinite(float _X) restrict(amp);
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
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nenulovou hodnotu, pokud argument má hodnotu NaN.  
  
##  <a name="ldexp"></a>  ldexp –  
 Vypočítá reálné číslo z mantisa a exponent  
  
```  
inline float ldexp(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou, mentissa  
  
 `_Exp`  
 Exponent celé číslo  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X * 2 ^ _Exp  
  
##  <a name="ldexpf"></a>  ldexpf –  
 Vypočítá reálné číslo z mantisa a exponent  
  
```  
inline float ldexpf(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou, mentissa  
  
 `_Exp`  
 Exponent celé číslo  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X * 2 ^ _Exp  
  
##  <a name="log"></a>  Protokolu  
 Vypočítá základní e logaritmus argumentu  
  
```  
inline float log(float _X) restrict(amp);
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
  
##  <a name="log2"></a>  log2  
 Vypočítá logaritmus o základu 2 argumentu  
  
```  
inline float log2(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí logaritmus o základu 2 argumentu  
  
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
 Rozdělí _X do zlomkové a částí celé číslo.  
  
```  
inline float modf(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Ip`  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí podepsaný část _X  
  
##  <a name="modff"></a>  modff –  
 Rozdělí _X do zlomkové a částí celé číslo.  
  
```  
inline float modff(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Ip`  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí podepsaný část _X  
  
##  <a name="pow"></a>  Pow  
 Vypočítá _X mocninu _Y  
  
```  
inline float pow(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou, základní  
  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou, exponentu  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu _X mocninu _Y  
  
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
  
##  <a name="round"></a>  Zaokrouhlit  
 Zaokrouhlí _X na nejbližší celé číslo  
  
```  
inline float round(float _X) restrict(amp);
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
  
##  <a name="signbit"></a>  signbit –  
 Určuje, zda je záporné znaménko _X  
  
```  
inline int signbit(float _X) restrict(amp);
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
    float* _S,  
    float* _C) restrict(amp);
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
    float* _S,  
    float* _C) restrict(amp);
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
  
##  <a name="sqrt"></a>  Sqrt  
 Vypočítá kořenu squre argumentu  
  
```  
inline float sqrt(float _X) restrict(amp);
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
  
##  <a name="trunc"></a>  TRUNC  
 Zkrátí argument pro komponentu celé číslo  
  
```  
inline float trunc(float _X) restrict(amp);
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

## <a name="requirements"></a>Požadavky
**Záhlaví:** amp_math.h **Namespace:** Concurrency::fast_math –
  
## <a name="see-also"></a>Viz také  
 [Concurrency::fast_math – obor názvů](concurrency-fast-math-namespace.md)
