---
title: omezení &lt;&gt; výčty
ms.date: 11/04/2016
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 567e0538f59c40d57f85d652a8919be6e034cf0b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420069"
---
# <a name="ltlimitsgt-enums"></a>omezení &lt;&gt; výčty

## <a name="float_denorm_style"></a>float_denorm_style

Výčet popisuje různé metody, které může implementace zvolit pro reprezentaci denormalizované hodnoty s plovoucí desetinnou čárkou – jedna je příliš malá, aby byla reprezentována jako normalizovaná hodnota:

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>Návratová hodnota

Výčet vrátí:

- `denorm_indeterminate`, pokud přítomnost denormalizovaných formulářů nemůže být určena v době překladu.

- v případě, že chybí denormalizované formuláře, `denorm_absent`.

- `denorm_present`, pokud jsou k dispozici denormalizované formuláře.

### <a name="example"></a>Příklad

Viz [numeric_limits:: has_denorm](../standard-library/numeric-limits-class.md#has_denorm) pro příklad, ve kterém je možné přistupovat k hodnotám tohoto výčtu.

## <a name="float_round_style"></a>float_round_style

Výčet popisuje různé metody, které může implementace zvolit pro zaokrouhlování hodnoty s plovoucí desetinnou čárkou na celočíselnou hodnotu.

```cpp
enum float_round_style {
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```

### <a name="return-value"></a>Návratová hodnota

Výčet vrátí:

- `round_indeterminate`, pokud nelze určit metodu zaokrouhlení.

- `round_toward_zero`, pokud se zaokrouhlí směrem k nule.

- `round_to_nearest`, pokud se zaokrouhlí na nejbližší celé číslo.

- `round_toward_infinity`, pokud se zaokrouhluje nula.

- `round_toward_neg_infinity`, pokud se zaokrouhlí na záporné celé číslo.

### <a name="example"></a>Příklad

Viz [numeric_limits:: round_style](../standard-library/numeric-limits-class.md#round_style) pro příklad, ve kterém je možné přistupovat k hodnotám tohoto výčtu.
