---
title: mersenne_twister_engine – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::mersenne_twister_engine
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
ms.openlocfilehash: ed5380e36e71d7366d2b4b84528bbd35b87cc775
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451864"
---
# <a name="mersennetwisterengine-class"></a>mersenne_twister_engine – třída

Generuje náhodnou posloupnost celých čísel na základě algoritmu Twister Mersenne.

## <a name="syntax"></a>Syntaxe

```cpp
template <class UIntType,
    size_t W, size_t N, size_t M, size_t R,
    UIntType A, size_t U, UIntType D, size_t S,
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>
class mersenne_twister_engine;
```

### <a name="parameters"></a>Parametry

*UIntType*\
Typ výsledku unsigned integer. Možné typy naleznete v tématu [ \<Random >](../standard-library/random.md).

*W*\
**Velikost slova**. Velikost každého slova v bitech sekvence stavů. **Předběžná podmínka**:`2u < W ≤ numeric_limits<UIntType>::digits`

*N*\
**Velikost stavu**. Počet elementů (hodnot) ve stavovém sekvenci.

*4M*\
**Velikost posunutí**. Počet prvků, které se mají přeskočit během každého otočení. **Předběžná podmínka**:`0 < M ≤ N`

*R*\
**Bity masky**. **Předběžná podmínka**:`R ≤ W`

*URČITÉHO*\
**Maska XOR**. **Předběžná podmínka**:`A ≤ (1u<<W) - 1u`

*U*, *S*, *T*, *L*\
**Přepouštění parametrů posunutí**. Používá se jako hodnota Shift při kódování (popouštění). Předběžná podmínka`U,S,T,L ≤ W`

*D*, *B*, *C*\
**Napouštění parametrů bitové masky**. Používá se jako hodnota bitové masky při kódování (napouštění). Předběžná podmínka`D,B,C ≤ (1u<<W) - 1u`

*FJ*\
**Multiplikátor inicializace**. Slouží k nápovědě při inicializaci sekvence. Předběžná podmínka`F ≤ (1u<<W) - 1u`

## <a name="members"></a>Členové

||||
|-|-|-|
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|

`default_seed`je členská konstanta definovaná jako `5489u`, používaná jako výchozí hodnota parametru pro `mersenne_twister_engine::seed` a konstruktor s jednou hodnotou.

Další informace o členech motoru naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Tato třída šablony popisuje modul náhodného čísla, který vrací hodnoty v uzavřeném intervalu `0`[ `2`, <sup>W</sup> - `1`]. Obsahuje velkou celočíselnou hodnotu s `W * (N - 1) + R` bity. Extrahuje *W* bity z této velké hodnoty a při použití všech bitů se tato velká hodnota posouvá posunutím a kombinováním bitů, aby byla k dispozici nová sada bitů pro extrakci. `N` Stav motoru jsou poslední `W`bitové hodnoty, `operator()` Pokud byla `N - M` `M` volána nejméně *N* krát, jinak bitovéhodnoty,kterébylypoužityaposledníhodnoty`W` sazení.

Generátor vytvoří velkou hodnotu, kterou udržuje, pomocí uživatelsky definovaného registru pro posunutí zpětné vazby, který je definovaný hodnotami Shift *N* a *M*, hodnotou otočení *R*a podmíněnou maskou XOR *a*. Kromě toho jsou bity nezpracovaného směny překódované (z pořízeného) podle bitové sady, která je definována hodnotami *U*, *D*, *S*, *B*, *T*, *C*a *L*.

Argument `UIntType` šablony musí být dostatečně velký, aby mohl uchovávat hodnoty až `2`do <sup>W</sup> - `1`. Hodnoty ostatních argumentů šablony musí splňovat následující požadavky: `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.

I když můžete vytvořit generátor z tohoto stroje přímo, doporučujeme použít jednu z těchto předdefinovaných definice typedef:

`mt19937`: 32-bit Mersenne Twister Engine (Matsumoto a Nishimura, 1998).

```cpp
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,
    31, 0x9908b0df,
    11, 0xffffffff,
    7, 0x9d2c5680,
    15, 0xefc60000,
    18, 1812433253> mt19937;
```

`mt19937_64`: 64-bit Mersenne Twister Engine (Matsumoto a Nishimura, 2000).

```cpp
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,
    31, 0xb5026f5aa96619e9ULL,
    29, 0x5555555555555555ULL,
    17, 0x71d67fffeda60000ULL,
    37, 0xfff7eee000000000ULL,
    43, 6364136223846793005ULL> mt19937_64;
```

Podrobné informace o algoritmu Twister Mersenne naleznete v článku Wikipedii [Mersenne Twister](https://go.microsoft.com/fwlink/p/?linkid=402356).

## <a name="example"></a>Příklad

Příklad kódu naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="requirements"></a>Požadavky

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
