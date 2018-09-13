---
title: subtract_with_carry_engine – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bfb0c3c0544a9c58801f98567825e7e97e48b13c
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "43687984"
---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine – třída

Generuje náhodné pořadí pomocí algoritmu subtract s carry (opožděné Fibonacciho).

## <a name="syntax"></a>Syntaxe

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>Parametry

*UIntType*  
 Typ výsledku celého čísla bez znaménka. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

*W*  
 **Word velikost**. Velikost jednotlivých slov v bitech, stav pořadí. **Předběžná podmínka**: `0 < W ≤ numeric_limits<UIntType>::digits`

*S*  
 **Krátká prodleva**. Počet hodnot typu integer. **Předběžná podmínka**: `0 < S < R`

*R*  
 **Dlouhá zpoždění**. Určuje opakování v řadě vygenerována.

## <a name="members"></a>Členové

||||
|-|-|-|
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|
|`default_seed` je členem konstantní, definované jako `19780503u`, která se používá jako výchozí hodnota parametru pro `subtract_with_carry_engine::seed` a konstruktoru jednu hodnotu.|||

Další informace o členech modul, naleznete v tématu [ \<náhodné >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

`substract_with_carry_engine` Třída šablony je vylepšením oproti [linear_congruential_engine –](../standard-library/linear-congruential-engine-class.md). Ani pro tyto moduly je tak rychle, nebo se jako výsledky vysoce kvalitní, jako [mersenne_twister_engine –](../standard-library/mersenne-twister-engine-class.md).

Tento modul vytváří hodnoty uživatelem zadaného bez znaménka integrálového typu pomocí vztahu opakování ( *období*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, kde `cy(i)` má hodnotu `1` Pokud `x(i - S) - x(i - R) - cy(i - 1) < 0`, jinak `0`, a `M` má hodnotu `2` <sup>W</sup>. Stav stroje je provádět indikátor plus *R* hodnoty. Tyto hodnoty se skládají z poslední *R* hodnoty vrácené if `operator()` byla volána alespoň *R* krát, jinak `N` hodnoty, které byly vráceny a poslední `R - N` hodnot seedu.

Argument šablony `UIntType` musí být dostatečně velký pro uložení hodnot až do `M - 1`.

I když generátor tento modul můžete vytvořit přímo, můžete použít také jednu z těchto předdefinovaných – definice TypeDef:

`ranlux24_base`: Používá se jako základ pro `ranlux24`.
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base`: Používá se jako základ pro `ranlux48`.
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

Podrobné informace o subract s algoritmem carry modul najdete v článku na wikipedii [zaostávalo kvůli Fibonacciho generátor](https://en.wikipedia.org/wiki/Lagged_Fibonacci_generator).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
