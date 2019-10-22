---
title: subtract_with_carry_engine – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
ms.openlocfilehash: 63cbbb3a1a508b41c1e0632eda3eeabe4fda6696
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685822"
---
# <a name="subtract_with_carry_engine-class"></a>subtract_with_carry_engine – třída

Vygeneruje náhodnou posloupnost pomocí algoritmu "odečíst" s přenesenou Fibonacci ().

## <a name="syntax"></a>Syntaxe

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>Parametry

*UIntType* \
Typ výsledku unsigned integer. Možné typy najdete v tématu [\<random >](../standard-library/random.md).

*W* \
**Velikost slova**. Velikost každého slova v bitech sekvence stavů. **Předběžná podmínka**: `0 < W ≤ numeric_limits<UIntType>::digits`

*S* \
**Krátká prodleva**. Počet celočíselných hodnot. **Předběžná podmínka**: `0 < S < R`

@No__t_1 *R*
**Dlouhá prodleva** Určuje opakování ve vygenerované řadě.

## <a name="members"></a>Členové

||||
|-|-|-|
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|
|`default_seed` je členská konstanta definovaná jako `19780503u`, která se používá jako výchozí hodnota parametru pro `subtract_with_carry_engine::seed` a konstruktor s jednou hodnotou.|||

Další informace o členech motoru naleznete v tématu [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Šablona třídy `substract_with_carry_engine` je zdokonalena nad [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md). Ani u těchto motorů není pro tyto moduly jako [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md)k dishornímu nebo jako vysoce kvalitní výsledky.

Tento modul vytvoří hodnoty uživatelem zadaného typu bez znaménka pomocí relace opakování ( *period*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, kde `cy(i)` má hodnotu `1` Pokud `x(i - S) - x(i - R) - cy(i - 1) < 0`, jinak `0` a `M` má hodnotu `2`<sup>W</sup>. Stav stroje je ukazatel s příznakem přenosu a hodnotou *R* . Tyto hodnoty se skládají z posledních hodnot *r* vrácených v případě, že `operator()` byla volána nejméně *R* krát, v opačném případě `N` vrácených hodnot a poslední `R - N` hodnot počáteční hodnoty.

Argument šablony `UIntType` musí být dostatečně velký, aby mohl uchovávat hodnoty až do `M - 1`.

I když můžete vytvořit generátor z tohoto stroje přímo, můžete také použít jeden z těchto předdefinovaných definice typedef:

`ranlux24_base`: používá se jako základ pro `ranlux24`.
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base`: používá se jako základ pro `ranlux48`.
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

Podrobné informace o subractu s algoritmem provozního modulu najdete v článku o Wikipedii [generátoru Fibonacci](https://en.wikipedia.org/wiki/Lagged_Fibonacci_generator).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<random >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<random >](../standard-library/random.md)
