---
title: mersenne_twister_engine – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- random/std::mersenne_twister_engine
dev_langs:
- C++
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc9d468f60b3e5f4fcf691e7397a5f7c0ce57089
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="mersennetwisterengine-class"></a>mersenne_twister_engine – třída

Generuje náhodné posloupnost celých čísel založený na algoritmu twister Mersenne, vysoké kvality.

## <a name="syntax"></a>Syntaxe

```cpp
template <class UIntType,
    size_t W, size_t N, size_t M, size_t R,
    UIntType A, size_t U, UIntType D, size_t S,
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>
class mersenne_twister_engine;
```

### <a name="parameters"></a>Parametry

`UIntType` Výsledný typ celé číslo bez znaménka. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).

`W` **Aplikace Word velikost**. Velikost jednotlivých slov v bitech, pořadí stavu. **Předběžnou**: `2u < W ≤ numeric_limits<UIntType>::digits`

`N` **Velikost stavu**. Počet elementů (hodnoty) v pořadí stavu.

`M` **Posunutí velikost**. Počet elementů při každém Točitost přeskočit. **Předběžnou**: `0 < M ≤ N`

`R` **Maskování bitů**. **Předběžnou**: `R ≤ W`

`A` **XOR maska**. **Předběžnou**: `A ≤ (1u<<W) - 1u`

`U`, `S`, `T`, `L` **Tempering shift parametry**. Použít jako hodnoty posunutí při kódování (popouštění). Předběžnou podmínku: `U,S,T,L ≤ W`

`D`, `B`, `C` **Tempering bit masky parametry**. Použít jako hodnoty bit masky při kódování (popouštění). Předběžnou podmínku: `D,B,C ≤ (1u<<W) - 1u`

`F` **Inicializace násobitel**. Použít k s inicializací pořadí. Předběžnou podmínku: `F ≤ (1u<<W) - 1u`

## <a name="members"></a>Členové

||||
|-|-|-|
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|

`default_seed` je členem konstantní, definované jako `5489u`, použít jako výchozí hodnota parametru pro `mersenne_twister_engine::seed` a konstruktor jednu hodnotu.

Další informace o modulu členy najdete v tématu [ \<náhodných >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato třída šablony popisuje náhodné číslo modul vrací hodnoty v intervalu uzavřené [ `0`, `2` <sup>W</sup> - `1`]. Drží velké celočíselné hodnoty s `W * (N - 1) + R` bits. Extrahuje `W` bits současně z této velké hodnoty, a pokud se má použít službu bits ho twists velké hodnoty s posunem a kombinování bity tak, aby měl novou sadu bitů extrahovat z. Stav stroje je poslední `N` `W`-bit hodnoty použít v případě `operator()` byla volána alespoň `N` krát jinak `M` `W`-bit hodnoty, které již byly použity a poslední `N - M` hodnoty z počáteční hodnoty.

Generátor twists vysokou hodnotu, která drží pomocí registru shift kroucená zobecněný zpětnou vazbu definované hodnoty posunutí `N` a `M`, hodnotu zákrutu `R`a podmíněného XOR maska `A`. Kromě toho jsou bity registru nezpracovaná shift kódována (zmírněna) podle kódování bit matice definované hodnoty `U`, `D`, `S`, `B`, `T`, `C`, a `L`.

Argument šablony `UIntType` musí být dostatečně velký pro uložení hodnoty až `2` <sup>W</sup> - `1`. Hodnoty jiné šablony argumentů musí splňovat následující požadavky: `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.

I když můžete vytvořit generátor z tento modul přímo, doporučuje se, že použijete jednu z těchto předdefinovaných definice TypeDef:

`mt19937`: 32-bit Mersenne twister modulu (Matsumoto a Nishimura, 1998).

```cpp
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,
    31, 0x9908b0df,
    11, 0xffffffff,
    7, 0x9d2c5680,
    15, 0xefc60000,
    18, 1812433253> mt19937;
```

`mt19937_64`: 64-bit Mersenne twister modulu (Matsumoto a Nishimura 2000).

```cpp
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,
    31, 0xb5026f5aa96619e9ULL,
    29, 0x5555555555555555ULL,
    17, 0x71d67fffeda60000ULL,
    37, 0xfff7eee000000000ULL,
    43, 6364136223846793005ULL> mt19937_64;
```

Podrobné informace o algoritmus twister Mersenne, najdete v článku Wikipedia [Mersenne twister](http://go.microsoft.com/fwlink/p/?linkid=402356).

## <a name="example"></a>Příklad

Příklad kódu, najdete v části [ \<náhodných >](../standard-library/random.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodných >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[\<náhodné >](../standard-library/random.md)<br/>
