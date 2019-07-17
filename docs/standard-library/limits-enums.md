---
title: '&lt;omezení&gt; výčty'
ms.date: 11/04/2016
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 567e0538f59c40d57f85d652a8919be6e034cf0b
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245358"
---
# <a name="ltlimitsgt-enums"></a>&lt;omezení&gt; výčty

## <a name="float_denorm_style"></a> float_denorm_style

Výčet popisuje různé metody, které můžete vybrat implementaci představující hodnotu s plovoucí desetinnou čárkou Nenormalizovaná – jeden příliš malá, aby reprezentovala normalizovanou hodnotu:

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>Návratová hodnota

Vrátí výčet:

- `denorm_indeterminate` Pokud v době překlad nelze určit přítomnosti nebo nepřítomnosti Nenormalizovaná formulářů.

- `denorm_absent` Pokud jsou Nenormalizovaná formuláře chybí.

- `denorm_present` Pokud jsou k dispozici Nenormalizovaná formuláře.

### <a name="example"></a>Příklad

Zobrazit [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm) pro příklad, ve kterém můžete získat přístup hodnoty tento výčet.

## <a name="float_round_style"></a> float_round_style

Výčet popisuje různé metody, které můžete vybrat implementaci při zaokrouhlení s plovoucí desetinnou čárkou na celočíselnou hodnotu.

```cpp
enum float_round_style {
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```

### <a name="return-value"></a>Návratová hodnota

Vrátí výčet:

- `round_indeterminate` Pokud nelze určit metodu zaokrouhlení.

- `round_toward_zero` Pokud kruhové směrem k nule.

- `round_to_nearest` Pokud zaokrouhlit na nejbližší celé číslo.

- `round_toward_infinity` Pokud kruhové směrem od nuly.

- `round_toward_neg_infinity` Pokud kruhové více záporné celé číslo.

### <a name="example"></a>Příklad

Zobrazit [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style) pro příklad, ve kterém můžete získat přístup hodnoty tento výčet.
