---
title: mersenne_twister_engine – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::mersenne_twister_engine
dev_langs:
- C++
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb03b35ed792bda7c506fd06d6102dda83c768e6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959268"
---
# <a name="mersennetwisterengine-class"></a>mersenne_twister_engine – třída

Generuje náhodné posloupnosti vysoce kvalitní celých čísel podle algoritmu twister Mersenne.

## <a name="syntax"></a>Syntaxe

```cpp
template <class UIntType,
    size_t W, size_t N, size_t M, size_t R,
    UIntType A, size_t U, UIntType D, size_t S,
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>
class mersenne_twister_engine;
```

### <a name="parameters"></a>Parametry

*UIntType* celé číslo bez znaménka typu výsledku. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

*W* **Word velikost**. Velikost jednotlivých slov v bitech, stav pořadí. **Předběžná podmínka**: `2u < W ≤ numeric_limits<UIntType>::digits`

*N* **stavu velikost**. Počet elementů (hodnoty) v pořadí stavu.

*M* **Shift velikost**. Počet prvků, které mají přeskočit při každé prvkem. **Předběžná podmínka**: `0 < M ≤ N`

*R* **maskování bitů**. **Předběžná podmínka**: `R ≤ W`

*A* **XOR maska**. **Předběžná podmínka**: `A ≤ (1u<<W) - 1u`

*U*, *S*, *T*, *L* **Tempering shift parametry**. Použít jako hodnoty shift při kódování (popouštění). Předběžné podmínky: `U,S,T,L ≤ W`

*D*, *B*, *C* **Tempering bitová maska parametry**. Používá se jako hodnoty bitové masky při kódování (popouštění). Předběžné podmínky: `D,B,C ≤ (1u<<W) - 1u`

*F* **inicializace multiplikátor**. Využít k s inicializací pořadí. Předběžné podmínky: `F ≤ (1u<<W) - 1u`

## <a name="members"></a>Členové

||||
|-|-|-|
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|

`default_seed` je členem konstantní, definované jako `5489u`, která se používá jako výchozí hodnota parametru pro `mersenne_twister_engine::seed` a konstruktoru jednu hodnotu.

Další informace o členech modul, naleznete v tématu [ \<náhodné >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato třída šablony Popisuje modul náhodných čísel, vrací hodnoty v uzavřeném intervalu [ `0`, `2` <sup>W</sup> - `1`]. Obsahuje velkou celočíselnou hodnotu s `W * (N - 1) + R` bits. Extrahuje *W* bitů současně z této velké hodnoty, a pokud použije všechny bity se otočí velkou hodnotu posunem a mícháním bitů tak, aby byly nové sady bitů pro extrakci. Stav stroje je poslední `N` `W`– bitová hodnota, pokud `operator()` byla volána alespoň *N* krát, jinak `M` `W`-bit, hodnoty, které již byly použity a posledních `N - M` hodnot seedu.

Generátor otočí velkou hodnotu, která obsahuje pomocí registru shift kroucená zobecněný zpětné vazby definované hodnoty posunu *N* a *M*, hodnota prvkem *R*a Podmíněné XOR maska *A*. Kromě toho jsou bity registru nezpracovaná shift zamíchal (korigovat) podle matice bit kódování definované hodnoty *U*, *D*, *S*, *B* , *T*, *C*, a *L*.

Argument šablony `UIntType` musí být dostatečně velký pro uložení hodnot až do `2` <sup>W</sup> - `1`. Hodnoty ostatních argumentů šablony musí splňovat následující požadavky: `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.

I když generátor tento modul můžete vytvořit přímo, doporučujeme že použít jednu z těchto předdefinovaných – definice TypeDef:

`mt19937`: 32-bit modulu twister Mersenne (Matsumoto a Nishimura 1998).

```cpp
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,
    31, 0x9908b0df,
    11, 0xffffffff,
    7, 0x9d2c5680,
    15, 0xefc60000,
    18, 1812433253> mt19937;
```

`mt19937_64`: 64-bit modulu twister Mersenne (Matsumoto a Nishimura 2000).

```cpp
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,
    31, 0xb5026f5aa96619e9ULL,
    29, 0x5555555555555555ULL,
    17, 0x71d67fffeda60000ULL,
    37, 0xfff7eee000000000ULL,
    43, 6364136223846793005ULL> mt19937_64;
```

Podrobné informace o algoritmu twister Mersenne, najdete v článku na wikipedii [Mersenne twister](http://go.microsoft.com/fwlink/p/?linkid=402356).

## <a name="example"></a>Příklad

Příklad kódu naleznete v tématu [ \<náhodné >](../standard-library/random.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
