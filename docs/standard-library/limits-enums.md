---
title: '&lt;omezení&gt; výčty | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 356c98ce5c93d1e05a583fc30c4758c5d15d7529
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858156"
---
# <a name="ltlimitsgt-enums"></a>&lt;omezení&gt; výčty

|||
|-|-|
|[float_denorm_style –](#float_denorm_style)|[float_round_style –](#float_round_style)|

## <a name="float_denorm_style"></a>  float_denorm_style – výčet

Výčet popisuje různé metody, které můžete vybrat implementace pro představující hodnotu s plovoucí desetinnou čárkou nenormalizované – jeden příliš malá, aby představují jako normalizovanou hodnotu:

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>Návratová hodnota

Vrátí výčet:

- **denorm_indeterminate** Pokud nelze určit existenci nebo neexistenci těchto nenormalizované forms v době překlad.

- **denorm_absent** Pokud nenormalizované formuláře chybí.

- **denorm_present** Pokud nenormalizované formulářů.

### <a name="example"></a>Příklad

V tématu [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm) příklad, ve kterém můžete získat přístup hodnoty tento výčet.

## <a name="float_round_style"></a>  float_round_style – výčet

Výčet popisuje různé metody, které můžete vybrat implementace pro zaokrouhlení hodnotu s plovoucí desetinnou čárkou na celočíselnou hodnotu.

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

- **round_indeterminate** Pokud nelze určit způsob zaokrouhlení.

- **round_toward_zero** Pokud odezvy směrem k nule.

- **round_to_nearest** Pokud zaokrouhlit na nejbližší celé číslo.

- **round_toward_infinity** Pokud odezvy směrem od nuly.

- **round_toward_neg_infinity** Pokud odezvy na více záporné celé číslo.

### <a name="example"></a>Příklad

V tématu [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style) příklad, ve kterém můžete získat přístup hodnoty tento výčet.

## <a name="see-also"></a>Viz také

[\<omezení >](../standard-library/limits.md)<br/>
