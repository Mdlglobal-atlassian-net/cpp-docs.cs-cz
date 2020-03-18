---
title: '&lt;náhodné&gt; funkce'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419642"
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
Celočíselný typ s plovoucí desetinnou čárkou. Možné typy naleznete v tématu [\<random >](../standard-library/random.md).

\ *BITS*
Počet bitů náhodnosti, které se mají použít.

\ *generátoru*
Třída generátoru náhodných čísel.

*Obecné*\
Odkaz na instanci generátoru náhodných čísel typu *generátor*.

### <a name="remarks"></a>Poznámky

Funkce šablony volá `operator()` pro *Obecné* opakované operace a zabalí vrácené hodnoty do hodnoty s plovoucí desetinnou čárkou `x` typu *RealType* , dokud neshromáždí zadaný počet bitů mantisy v `x`. Zadané číslo je menší z *bitů* (které musí být nenulové) a plný počet bitů mantisy v *RealType*. První volání dodá nejnižší počet bitů. Funkce vrátí `x`.
