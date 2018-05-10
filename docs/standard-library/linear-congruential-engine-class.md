---
title: linear_congruential_engine – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::linear_congruential_engine
dev_langs:
- C++
helpviewer_keywords:
- linear_congruential_engine class
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f902e7a1a3ae4bcb35a4822228425747476d5bc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="linearcongruentialengine-class"></a>linear_congruential_engine – třída

Generuje náhodné pořadí lineární congruential algoritmem.

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

`UIntType` Výsledný typ celé číslo bez znaménka. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).

`A` **Násobitel**. **Předběžnou**: oddílu najdete v části poznámky.

`C` **Přírůstek**. **Předběžnou**: oddílu najdete v části poznámky.

`M` **MODULUS**. **Předběžnou**: najdete v části poznámky.

## <a name="members"></a>Členové

||||
|-|-|-|
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|

`default_seed` je členem konstantní, definované jako `1u`, použít jako výchozí hodnota parametru pro `linear_congruential_engine::seed` a konstruktor jednu hodnotu.

Další informace o modulu členy najdete v tématu [ \<náhodných >](../standard-library/random.md).

## <a name="remarks"></a>Poznámky

`linear_congruential_engine` Třída šablony je nejjednodušší modul generátor, ale není kvality nejrychlejší nebo nejvyšší. Zlepšení přes tento modul je [substract_with_carry_engine](../standard-library/subtract-with-carry-engine-class.md). Žádná z těchto modulů není tak rychle, nebo s jako vysoce kvalitního výsledky jako [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).

Tento modul vytváří hodnoty typu zadán uživatel nepodepsaných integrálních pomocí vztahu opakování ( *období*) `x(i) = (A * x(i-1) + C) mod M`.

Pokud `M` rovná nule, je hodnota používaná pro tuto operaci numerického zbytku `numeric_limits<result_type>::max() + 1`. Stav stroje je poslední hodnota vrácená nebo počáteční hodnoty, pokud žádné volání do `operator()`.

Pokud `M` není nulový hodnoty argumentů šablony `A` a `C` musí být menší než `M`.

Přestože generátor z tento modul můžete vytvořit přímo, můžete také použít jednu z těchto předdefinovaných definice TypeDef.

`minstd_rand0`: 1988 minimální standardní modul (Lewis, Goodman a Lukeš, 1969).

```cpp
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
```

`minstd_rand`: Aktualizovaný minimální standardní modul `minstd_rand0` (parku, Lukeš a Stockmeyer, 1993).

```cpp
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
```

Podrobné informace o algoritmus lineární congruential modul, najdete v článku Wikipedia [lineární congruential generátor](http://go.microsoft.com/fwlink/p/?linkid=402446).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodných >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[\<náhodné >](../standard-library/random.md)<br/>
