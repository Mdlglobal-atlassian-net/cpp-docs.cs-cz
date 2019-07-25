---
title: linear_congruential_engine – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::linear_congruential_engine
helpviewer_keywords:
- linear_congruential_engine class
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
ms.openlocfilehash: f5b448fbf158cf9e9cfb8331c6ec7a228859fffc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447578"
---
# <a name="linearcongruentialengine-class"></a>linear_congruential_engine – třída

Vygeneruje náhodnou sekvenci lineárním algoritmem algoritmu congruential.

## <a name="syntax"></a>Syntaxe

```cpp
class linear_congruential_engine{
   public:  // types
   typedef UIntType result_type;
   // engine characteristics
   static constexpr result_type multiplier = a;
   static constexpr result_type increment = c;
   static constexpr result_type modulus = m;
   static constexpr result_type min() { return c == 0u  1u: 0u; }
   static constexpr result_type max() { return m - 1u; }
   static constexpr result_type default_seed = 1u;
   // constructors and seeding functions
   explicit linear_congruential_engine(result_type s = default_seed);
   template <class Sseq>
   explicit linear_congruential_engine(Sseq& q);
   void seed(result_type s = default_seed);
   template <class Sseq>
   void seed(Sseq& q);
   // generating functions
   result_type operator()();
   void discard(unsigned long long z);
   };
```

### <a name="parameters"></a>Parametry

*UIntType*\
Typ výsledku unsigned integer. Možné typy naleznete v tématu [ \<Random >](../standard-library/random.md).

*URČITÉHO*\
**Násobitel**. **Předběžná podmínka**: Viz část poznámky.

*R*\
**Přírůstek**: **Předběžná podmínka**: Viz část poznámky.

*4M*\
**Modulus**. **Předběžná podmínka**: Viz poznámky.

## <a name="members"></a>Členové

||||
|-|-|-|
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|

`default_seed`je členská konstanta definovaná jako `1u`, používaná jako výchozí hodnota parametru pro `linear_congruential_engine::seed` a konstruktor s jednou hodnotou.

Další informace o členech motoru naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

Třída `linear_congruential_engine` šablony je nejjednodušší modul generátoru, ale ne nejrychlejší nebo nejvyšší kvalita. Vylepšení tohoto stroje je [substract_with_carry_engine](../standard-library/subtract-with-carry-engine-class.md). Ani jeden z těchto modulů není rychlejší ani s vysokou kvalitou výsledků jako [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).

Tento modul vytvoří hodnoty uživatelem zadaného typu bez znaménka pomocí relace opakování ( *period*) `x(i) = (A * x(i-1) + C) mod M`.

Pokud je *M* nula, hodnota použitá pro tuto operaci zbytku je `numeric_limits<result_type>::max() + 1`. Stav stroje je poslední vrácená hodnota nebo hodnota počáteční hodnoty, pokud žádné volání nebylo provedeno `operator()`.

Pokud *M* není nula, hodnoty argumentů šablony *a* a *C* musí být menší než *M*.

I když můžete vytvořit generátor z tohoto stroje přímo, můžete také použít jeden z těchto předdefinovaných definice typedef.

`minstd_rand0`: 1988 minimální standardní stroj (Lewis, Goodman a Miller, 1969).

```cpp
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
```

`minstd_rand`: Byl aktualizován minimální standardní `minstd_rand0` stroj (Park, Miller a Stockmeyer, 1993).

```cpp
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
```

Podrobné informace o algoritmu lineárního algoritmu congruential modulu najdete v článku Wikipedii pro [lineární generátor algoritmu congruential](https://go.microsoft.com/fwlink/p/?linkid=402446).

## <a name="requirements"></a>Požadavky

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
