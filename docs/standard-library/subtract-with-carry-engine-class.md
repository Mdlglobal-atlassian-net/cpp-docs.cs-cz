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
ms.openlocfilehash: 17091e33c504df60c0b6b8e346d2a6fd3893679c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447419"
---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine – třída

Vygeneruje náhodnou posloupnost pomocí algoritmu "odečíst" s přenesenou Fibonacci ().

## <a name="syntax"></a>Syntaxe

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>Parametry

*UIntType*\
Typ výsledku unsigned integer. Možné typy naleznete v tématu [ \<Random >](../standard-library/random.md).

*W*\
**Velikost slova**. Velikost každého slova v bitech sekvence stavů. **Předběžná podmínka**:`0 < W ≤ numeric_limits<UIntType>::digits`

*PRACUJÍ*\
**Krátká prodleva**. Počet celočíselných hodnot. **Předběžná podmínka**:`0 < S < R`

*R*\
**Dlouhá prodleva** Určuje opakování ve vygenerované řadě.

## <a name="members"></a>Členové

||||
|-|-|-|
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|
|`default_seed`je členská konstanta definovaná jako `19780503u`, používaná jako výchozí hodnota parametru pro `subtract_with_carry_engine::seed` a konstruktor s jednou hodnotou.|||

Další informace o členech motoru naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Třída šablony je zlepšením v linear_congruential_engine. [](../standard-library/linear-congruential-engine-class.md) `substract_with_carry_engine` Ani u těchto motorů není pro tyto moduly jako [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md)k dishornímu nebo jako vysoce kvalitní výsledky.

Tento modul vytvoří hodnoty uživatelem zadaného typu bez znaménka pomocí relace opakování ( *period*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, kde `0` `cy(i)` má hodnotu `1` IF `x(i - S) - x(i - R) - cy(i - 1) < 0`, jinak a `M` má hodnotu `2` <sup>W</sup>. Stav stroje je ukazatel s příznakem přenosu a hodnotou *R* . Tyto hodnoty se skládají z posledních hodnot *r* vrácených `operator()` , pokud byla volána nejméně  `N` R krát, jinak hodnoty, které byly vráceny, a poslední `R - N` hodnoty osazení.

Argument `UIntType` šablony musí být dostatečně velký, aby mohl uchovávat hodnoty až `M - 1`do.

I když můžete vytvořit generátor z tohoto stroje přímo, můžete také použít jeden z těchto předdefinovaných definice typedef:

`ranlux24_base`: Používá se jako základ pro `ranlux24`.
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base`: Používá se jako základ pro `ranlux48`.
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

Podrobné informace o subractu s algoritmem provozního modulu najdete v článku o Wikipedii [generátoru Fibonacci](https://en.wikipedia.org/wiki/Lagged_Fibonacci_generator).

## <a name="requirements"></a>Požadavky

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
