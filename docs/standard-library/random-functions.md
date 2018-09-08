---
title: '&lt;náhodné&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: e01c1d71cbc0b3990e40a38484cc9c7a2cc3ebcc
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102795"
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
