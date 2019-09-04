---
title: '&lt;náhodné&gt; funkce'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273829"
---
# <a name="ltrandomgt-functions"></a>&lt;náhodné&gt; funkce

## <a name="generate_canonical"></a>generate_canonical

Vrátí hodnotu s plovoucí desetinnou čárkou z náhodné sekvence.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parametry

*RealType*\
Celočíselný typ s plovoucí desetinnou čárkou. Možné typy naleznete v tématu [ \<Random >](../standard-library/random.md).

*Bit*\
Počet bitů náhodnosti, které se mají použít.

*Zdrojové*\
Třída generátoru náhodných čísel.

*Pole*\
Odkaz na instanci generátoru náhodných čísel typu *generátor*.

### <a name="remarks"></a>Poznámky

Funkce šablony volá metodu `operator()` *gen* opakovaně a zabalí vrácené hodnoty do hodnoty `x` s plovoucí desetinnou čárkou typu *RealType* , dokud neshromáždí zadaný počet bitů mantisy v. `x` Zadané číslo je menší z *bitů* (které musí být nenulové) a plný počet bitů mantisy v *RealType*. První volání dodá nejnižší počet bitů. Funkce vrátí `x`.
