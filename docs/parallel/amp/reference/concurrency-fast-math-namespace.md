---
title: Concurrency::fast_math – obor názvů
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
ms.openlocfilehash: e774c2d8e4431960e796ee1e6cc87b924d04174b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405596"
---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math – obor názvů

Funkce v `fast_math` obor názvů mají nižší přesnost, podporují pouze jednoduchou přesnost (`float`) a volání vnitřní objekty rozhraní DirectX. Existují dvě verze jednotlivých funkcí, třeba `cos` a `cosf`. Obě verze přebírají a vracejí `float`, ale každá volá stejný DirectX vnitřní.

## <a name="syntax"></a>Syntaxe

```
namespace fast_math;
```

## <a name="members"></a>Členové

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|Vypočítá arkuskosinus argumentu|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Vypočítá arkuskosinus argumentu|
|[asin](concurrency-fast-math-namespace-functions.md#asin)|Vypočítá arkussinus argumentu|
|[asinf –](concurrency-fast-math-namespace-functions.md#asinf)|Vypočítá arkussinus argumentu|
|[atan](concurrency-fast-math-namespace-functions.md#atan)|Vypočítá arkustangens argumentu|
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|Vypočítá arkustangens výrazu _Y/_X|
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|Vypočítá arkustangens výrazu _Y/_X|
|[atanf –](concurrency-fast-math-namespace-functions.md#atanf)|Vypočítá arkustangens argumentu|
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|Vypočítá horní mez argumentu|
|[ceilf –](concurrency-fast-math-namespace-functions.md#ceilf)|Vypočítá horní mez argumentu|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|Vypočítá kosinus argumentu|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Vypočítá kosinus argumentu|
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|Vypočítá hodnotu hyperbolického kosinu argumentu|
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|Vypočítá hodnotu hyperbolického kosinu argumentu|
|[exp](concurrency-fast-math-namespace-functions.md#exp)|Vypočítá exponenciální funkci argumentu base-e|
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|Vypočítá exponenciální argumentu base-2|
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|Vypočítá exponenciální argumentu base-2|
|[expf](concurrency-fast-math-namespace-functions.md#expf)|Vypočítá exponenciální funkci argumentu base-e|
|[fabs –](concurrency-fast-math-namespace-functions.md#fabs)|Vrátí absolutní hodnotu argumentu|
|[fabsf –](concurrency-fast-math-namespace-functions.md#fabsf)|Vrátí absolutní hodnotu argumentu|
|[Dolní mez](concurrency-fast-math-namespace-functions.md#floor)|Vypočítá dolní mez argumentu|
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|Vypočítá dolní mez argumentu|
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|Určí maximální číselnou hodnotu argumentů|
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|Určí maximální číselnou hodnotu argumentů|
|[Fmin –](concurrency-fast-math-namespace-functions.md#fmin)|Určí minimální číselnou hodnotu argumentů|
|[fminf –](concurrency-fast-math-namespace-functions.md#fminf)|Určí minimální číselnou hodnotu argumentů|
|[Fmod –](concurrency-fast-math-namespace-functions.md#fmod)|Vypočítá zbytek s plovoucí desetinnou čárkou z výrazu _X/_Y|
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|Vypočítá zbytek s plovoucí desetinnou čárkou z výrazu _X/_Y|
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|Načte mantisu a exponent proměnné _X|
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|Načte mantisu a exponent proměnné _X|
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|Určuje, zda má argument konečnou hodnotu|
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|Určí, zda je argument nekonečno|
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|Určí, zda je argument NaN|
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|Vypočítá reálné číslo z mantisy a exponentu|
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|Vypočítá reálné číslo z mantisy a exponentu|
|[log](concurrency-fast-math-namespace-functions.md#log)|Vypočítá logaritmus argumentu o základu e|
|[log10](concurrency-fast-math-namespace-functions.md#log10)|Vypočítá logaritmus argumentu o základu 10|
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|Vypočítá logaritmus argumentu o základu 10|
|[log2](concurrency-fast-math-namespace-functions.md#log2)|Vypočítá logaritmus argumentu o základu 2|
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|Vypočítá logaritmus argumentu o základu 2|
|[logf](concurrency-fast-math-namespace-functions.md#logf)|Vypočítá logaritmus argumentu o základu e|
|[modf](concurrency-fast-math-namespace-functions.md#modf)|Rozdělí _X na frakce a celá čísla.|
|[modff](concurrency-fast-math-namespace-functions.md#modff)|Rozdělí _X na frakce a celá čísla.|
|[Pow](concurrency-fast-math-namespace-functions.md#pow)|Vypočítá proměnnou _X umocněnou exponentem _y|
|[powf](concurrency-fast-math-namespace-functions.md#powf)|Vypočítá proměnnou _X umocněnou exponentem _y|
|[Zaokrouhlit](concurrency-fast-math-namespace-functions.md#round)|Zaokrouhlí číslo _X na nejbližší celé číslo.|
|[roundf –](concurrency-fast-math-namespace-functions.md#roundf)|Zaokrouhlí číslo _X na nejbližší celé číslo.|
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|Vrátí převrácenou hodnotu druhé odmocniny argumentu|
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|Vrátí převrácenou hodnotu druhé odmocniny argumentu|
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|Vrátí znaménko argumentu|
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|Vrátí znaménko argumentu|
|[sin](concurrency-fast-math-namespace-functions.md#sin)|Vypočítá hodnotu sinu argumentu|
|[sincos –](concurrency-fast-math-namespace-functions.md#sincos)|Vypočítá hodnotu sinu a kosinu proměnné _x|
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|Vypočítá hodnotu sinu a kosinu proměnné _x|
|[sinf –](concurrency-fast-math-namespace-functions.md#sinf)|Vypočítá hodnotu sinu argumentu|
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|Vypočítá hodnotu hyperbolického sinu argumentu|
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|Vypočítá hodnotu hyperbolického sinu argumentu|
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|Vypočítá druhou odmocninu argumentu|
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|Vypočítá druhou odmocninu argumentu|
|[Tan](concurrency-fast-math-namespace-functions.md#tan)|Vypočítá hodnotu tangentu argumentu|
|[tanf –](concurrency-fast-math-namespace-functions.md#tanf)|Vypočítá hodnotu tangentu argumentu|
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|Vypočítá hodnotu hyperbolického tangentu argumentu|
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|Vypočítá hodnotu hyperbolického tangentu argumentu|
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|Ořízne argument na celé číslo součásti|
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|Ořízne argument na celé číslo součásti|

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_math.h

**Namespace:** Concurrency::fast_math

## <a name="see-also"></a>Viz také:

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
