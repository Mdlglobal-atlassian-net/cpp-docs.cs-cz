---
title: Concurrency::fast_math – obor názvů
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
ms.openlocfilehash: 57e2134a2254dc4bc34d515e65e2ec629efeff33
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139510"
---
# <a name="concurrencyfast_math-namespace"></a>Concurrency::fast_math – obor názvů

Funkce v oboru názvů `fast_math` mají nižší přesnost, podporují pouze jednoduchou přesnost (`float`) a volají vnitřní objekty rozhraní DirectX. Existují dvě verze každé funkce, například `cos` a `cosf`. Obě verze přebírají a vracejí `float`, ale každé volá stejné vnitřní rozhraní DirectX.

## <a name="syntax"></a>Syntaxe

```cpp
namespace fast_math;
```

## <a name="members"></a>Členové

### <a name="functions"></a>Functions

|Název|Popis|
|----------|-----------------|
|[Cos](concurrency-fast-math-namespace-functions.md#cos)|Vypočítá Arkus kosinus argumentu.|
|[cosf –](concurrency-fast-math-namespace-functions.md#cosf)|Vypočítá Arkus kosinus argumentu.|
|[ASIN](concurrency-fast-math-namespace-functions.md#asin)|Vypočítá Arkus sinus argumentu.|
|[asinf –](concurrency-fast-math-namespace-functions.md#asinf)|Vypočítá Arkus sinus argumentu.|
|[atan](concurrency-fast-math-namespace-functions.md#atan)|Vypočítá arkustangens argumentu|
|[funkce](concurrency-fast-math-namespace-functions.md#atan2)|Vypočítá arkustangens _Y/_X|
|[atan2f –](concurrency-fast-math-namespace-functions.md#atan2f)|Vypočítá arkustangens _Y/_X|
|[atanf –](concurrency-fast-math-namespace-functions.md#atanf)|Vypočítá arkustangens argumentu|
|[ceil –](concurrency-fast-math-namespace-functions.md#ceil)|Vypočítá strop argumentu.|
|[ceilf –](concurrency-fast-math-namespace-functions.md#ceilf)|Vypočítá strop argumentu.|
|[Cos](concurrency-fast-math-namespace-functions.md#cos)|Vypočítá kosinus argumentu.|
|[cosf –](concurrency-fast-math-namespace-functions.md#cosf)|Vypočítá kosinus argumentu.|
|[cosh –](concurrency-fast-math-namespace-functions.md#cosh)|Vypočítá hodnotu hyperbolický kosinus argumentu.|
|[coshf –](concurrency-fast-math-namespace-functions.md#coshf)|Vypočítá hodnotu hyperbolický kosinus argumentu.|
|[oček](concurrency-fast-math-namespace-functions.md#exp)|Vypočítá exponenciální hodnotu argumentu (Base-e).|
|[exp2 –](concurrency-fast-math-namespace-functions.md#exp2)|Vypočítá exponenciální hodnotu argumentu o základu 2.|
|[exp2f –](concurrency-fast-math-namespace-functions.md#exp2f)|Vypočítá exponenciální hodnotu argumentu o základu 2.|
|[expf –](concurrency-fast-math-namespace-functions.md#expf)|Vypočítá exponenciální hodnotu argumentu (Base-e).|
|[fabs –](concurrency-fast-math-namespace-functions.md#fabs)|Vrátí absolutní hodnotu argumentu.|
|[fabsf –](concurrency-fast-math-namespace-functions.md#fabsf)|Vrátí absolutní hodnotu argumentu.|
|[řízení](concurrency-fast-math-namespace-functions.md#floor)|Vypočítá podlahu argumentu.|
|[floorf –](concurrency-fast-math-namespace-functions.md#floorf)|Vypočítá podlahu argumentu.|
|[Fmax –](concurrency-fast-math-namespace-functions.md#fmax)|Určení maximální číselné hodnoty argumentů|
|[fmaxf –](concurrency-fast-math-namespace-functions.md#fmaxf)|Určení maximální číselné hodnoty argumentů|
|[fmin –](concurrency-fast-math-namespace-functions.md#fmin)|Určení minimální číselné hodnoty argumentů|
|[fminf –](concurrency-fast-math-namespace-functions.md#fminf)|Určení minimální číselné hodnoty argumentů|
|[FMOD –](concurrency-fast-math-namespace-functions.md#fmod)|Vypočítá zbytek _X/_Y s plovoucí desetinnou čárkou.|
|[fmodf –](concurrency-fast-math-namespace-functions.md#fmodf)|Vypočítá zbytek _X/_Y s plovoucí desetinnou čárkou.|
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|Získá mantisu a exponent _X.|
|[frexpf –](concurrency-fast-math-namespace-functions.md#frexpf)|Získá mantisu a exponent _X.|
|[isfinite –](concurrency-fast-math-namespace-functions.md#isfinite)|Určuje, zda má argument konečnou hodnotu.|
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|Určuje, zda je argumentem nekonečno.|
|[IsNaN](concurrency-fast-math-namespace-functions.md#isnan)|Určuje, zda je argumentem hodnota NaN.|
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|Vypočítá reálné číslo z mantisy a exponentu.|
|[ldexpf –](concurrency-fast-math-namespace-functions.md#ldexpf)|Vypočítá reálné číslo z mantisy a exponentu.|
|[protokolu](concurrency-fast-math-namespace-functions.md#log)|Vypočítá logaritmus argumentu o základu e.|
|[log10 –](concurrency-fast-math-namespace-functions.md#log10)|Vypočítá logaritmus argumentu o základu 10.|
|[log10f –](concurrency-fast-math-namespace-functions.md#log10f)|Vypočítá logaritmus argumentu o základu 10.|
|[log2 –](concurrency-fast-math-namespace-functions.md#log2)|Vypočítá logaritmus argumentu o základu 2.|
|[log2f –](concurrency-fast-math-namespace-functions.md#log2f)|Vypočítá logaritmus argumentu o základu 2.|
|[logf –](concurrency-fast-math-namespace-functions.md#logf)|Vypočítá logaritmus argumentu o základu e.|
|[modf –](concurrency-fast-math-namespace-functions.md#modf)|Rozdělí _X do zlomkové a celočíselné části.|
|[modff –](concurrency-fast-math-namespace-functions.md#modff)|Rozdělí _X do zlomkové a celočíselné části.|
|[log](concurrency-fast-math-namespace-functions.md#pow)|Vypočítá _X umocněnou mocninou _Y|
|[powf –](concurrency-fast-math-namespace-functions.md#powf)|Vypočítá _X umocněnou mocninou _Y|
|[zpoždění](concurrency-fast-math-namespace-functions.md#round)|Zaokrouhlí _X na nejbližší celé číslo.|
|[roundf –](concurrency-fast-math-namespace-functions.md#roundf)|Zaokrouhlí _X na nejbližší celé číslo.|
|[rsqrt –](concurrency-fast-math-namespace-functions.md#rsqrt)|Vrátí převrácenou druhou odmocninu argumentu.|
|[rsqrtf –](concurrency-fast-math-namespace-functions.md#rsqrtf)|Vrátí převrácenou druhou odmocninu argumentu.|
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|Vrátí znaménko argumentu.|
|[signbitf –](concurrency-fast-math-namespace-functions.md#signbitf)|Vrátí znaménko argumentu.|
|[tlačítek](concurrency-fast-math-namespace-functions.md#sin)|Vypočítá hodnotu sinus argumentu|
|[sincos –](concurrency-fast-math-namespace-functions.md#sincos)|Vypočítá hodnotu sinus a kosinus _X|
|[sincosf –](concurrency-fast-math-namespace-functions.md#sincosf)|Vypočítá hodnotu sinus a kosinus _X|
|[sinf –](concurrency-fast-math-namespace-functions.md#sinf)|Vypočítá hodnotu sinus argumentu|
|[sinh –](concurrency-fast-math-namespace-functions.md#sinh)|Vypočítá hodnotu hyperbolický sinus argumentu.|
|[sinhf –](concurrency-fast-math-namespace-functions.md#sinhf)|Vypočítá hodnotu hyperbolický sinus argumentu.|
|[SQRT](concurrency-fast-math-namespace-functions.md#sqrt)|Vypočítá druhou odmocninu argumentu.|
|[sqrtf –](concurrency-fast-math-namespace-functions.md#sqrtf)|Vypočítá druhou odmocninu argumentu.|
|[nádrž](concurrency-fast-math-namespace-functions.md#tan)|Vypočítá hodnotu tangens argumentu.|
|[tanf –](concurrency-fast-math-namespace-functions.md#tanf)|Vypočítá hodnotu tangens argumentu.|
|[tanh –](concurrency-fast-math-namespace-functions.md#tanh)|Vypočítá hodnotu hyperbolický tangens argumentu.|
|[tanhf –](concurrency-fast-math-namespace-functions.md#tanhf)|Vypočítá hodnotu hyperbolický tangens argumentu.|
|[TRUNC –](concurrency-fast-math-namespace-functions.md#trunc)|Zkrátí argument na celočíselnou komponentu.|
|[truncf –](concurrency-fast-math-namespace-functions.md#truncf)|Zkrátí argument na celočíselnou komponentu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_math. h

**Obor názvů:** Concurrency:: fast_math

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
