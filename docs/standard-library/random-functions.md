---
title: '&lt;náhodné&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 87b640d4f3aa3fbfa23ad5603d84102301e71ea4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240388"
---
# <a name="ltrandomgt-functions"></a>&lt;náhodné&gt; funkce

## <a name="generate_canonical"></a> generate_canonical

Vrátí hodnotu s plovoucí desetinnou čárkou v náhodném pořadí.

> [!NOTE]
> ISO C++ Standard uvádí, že tato funkce by měla vrátit hodnoty v rozsahu [ `0`, `1`). Visual Studio není kompatibilní s tímto omezením. Jako alternativní řešení pro generování hodnot v tomto rozsahu, použijte [uniform_real_distribution –](../standard-library/uniform-real-distribution-class.md).

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parametry

*RealType*\
S plovoucí desetinnou čárkou celočíselného typu. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

*Služba BITS*\
Generátor náhodných čísel.

*Obecné*\
Generátor náhodných čísel.

### <a name="remarks"></a>Poznámky

Volání šablony funkce `operator()` z *Obecné* opakovaně a sady vrácené hodnoty na hodnotu s plovoucí desetinnou čárkou `x` typu *RealType* dokud shromáždil zadané číslo mantisa bitů v `x`. Zadané číslo je menší z hodnot *Bits* (který musí být nenulové) a úplná počet bitů mantisa v *RealType*. První volání je zadán bits nejnižším pořadím. Funkce vrátí `x`.
