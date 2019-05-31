---
title: linear_congruential_engine – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::linear_congruential_engine
helpviewer_keywords:
- linear_congruential_engine class
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
ms.openlocfilehash: 41ce5590476a8327c9449ece5e3173146a04760f
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449902"
---
# <a name="linearcongruentialengine-class"></a>linear_congruential_engine – třída

Generuje náhodnou posloupnost pomocí lineárního algoritmu congruential.

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

*UIntType*<br/>
Typ výsledku celého čísla bez znaménka. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

*A*<br/>
**Násobitel**. **Předběžná podmínka**: Viz část poznámky.

*C*<br/>
**Přírůstek**. **Předběžná podmínka**: Viz část poznámky.

*M*<br/>
**MODULUS**. **Předběžná podmínka**: Viz poznámky.

## <a name="members"></a>Členové

||||
|-|-|-|
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|

`default_seed` je členem konstantní, definované jako `1u`, která se používá jako výchozí hodnota parametru pro `linear_congruential_engine::seed` a konstruktoru jednu hodnotu.

Další informace o členech modul, naleznete v tématu [ \<náhodné >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

`linear_congruential_engine` Třída šablony je nejjednodušší modul generátor, ale ne nejrychlejší nebo nejvyšší kvality. Vylepšení přes tento modul je [substract_with_carry_engine](../standard-library/subtract-with-carry-engine-class.md). Ani jeden z těchto modulů je tak rychle, nebo se jako výsledky vysoce kvalitní, jako [mersenne_twister_engine –](../standard-library/mersenne-twister-engine-class.md).

Tento modul vytváří hodnoty uživatelem zadaného bez znaménka integrálového typu pomocí vztahu opakování ( *období*) `x(i) = (A * x(i-1) + C) mod M`.

Pokud *M* je nula, je hodnota používaná pro tuto operaci numerického zbytku `numeric_limits<result_type>::max() + 1`. Stav stroje je poslední vrácená hodnota nebo počáteční hodnoty, pokud žádná volání do `operator()`.

Pokud *M* není nulový hodnoty argumentů šablon *A* a *C* musí být menší než *M*.

Přestože generátor tento modul můžete vytvořit přímo, můžete také použít jednu z těchto předdefinovaných – definice TypeDef.

`minstd_rand0`: 1988 minimální standard (Lewis, Goodman a modul Miller, 1969).

```cpp
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
```

`minstd_rand`: Aktualizovaný modul ochrany minimální standardní `minstd_rand0` (Park, Miller a Stockmeyer 1993).

```cpp
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
```

Podrobné informace o lineárního algoritmu congruential algoritmus, najdete v článku na wikipedii [lineární congruential generátor](https://go.microsoft.com/fwlink/p/?linkid=402446).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
