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
ms.openlocfilehash: 5b0cd634dad099669d803d4a2717fc9198151781
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954155"
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

*RealType* celočíselného typu s plovoucí desetinnou čárkou. Možné typy, najdete v části [ \<náhodné >](../standard-library/random.md).

*Služba BITS* generátor náhodných čísel.

*Obecné* generátor náhodných čísel.

### <a name="remarks"></a>Poznámky

Volání šablony funkce `operator()` z *Obecné* opakovaně a sady vrácené hodnoty na hodnotu s plovoucí desetinnou čárkou `x` typu *RealType* dokud shromáždil zadané číslo mantisa bitů v `x`. Zadané číslo je menší z hodnot *Bits* (který musí být nenulové) a úplná počet bitů mantisa v *RealType*. První volání je zadán bits nejnižším pořadím. Funkce vrátí `x`.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
