---
title: '&lt;náhodné&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 80bdb1ca83be5fb390035d7f3b005793a2f03715
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520611"
---
# <a name="ltrandomgt-functions"></a>&lt;náhodné&gt; funkce

## <a name="generate_canonical"></a>  generate_canonical

Vrátí hodnotu s plovoucí desetinnou čárkou v náhodném pořadí.

> [!NOTE]
> Norma ISO C++ uvádí, že tato funkce by měla vrátit hodnoty v rozsahu [ `0`, `1`). Visual Studio není kompatibilní s tímto omezením. Jako alternativní řešení pro generování hodnot v tomto rozsahu, použijte [uniform_real_distribution –](../standard-library/uniform-real-distribution-class.md).

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parametry

*RealType*<br/>
S plovoucí desetinnou čárkou celočíselného typu. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

*Služba BITS*<br/>
Generátor náhodných čísel.

*Obecné*<br/>
Generátor náhodných čísel.

### <a name="remarks"></a>Poznámky

Volání šablony funkce `operator()` z *Obecné* opakovaně a sady vrácené hodnoty na hodnotu s plovoucí desetinnou čárkou `x` typu *RealType* dokud shromáždil zadané číslo mantisa bitů v `x`. Zadané číslo je menší z hodnot *Bits* (který musí být nenulové) a úplná počet bitů mantisa v *RealType*. První volání je zadán bits nejnižším pořadím. Funkce vrátí `x`.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
