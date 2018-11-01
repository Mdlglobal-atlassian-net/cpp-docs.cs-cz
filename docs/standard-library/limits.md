---
title: '&lt;omezení&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: aa143198ec662ae33263d1ee5d79ffadf51c61d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632450"
---
# <a name="ltlimitsgt"></a>&lt;omezení&gt;

Třída šablony definuje `numeric_limits` a dvě výčty o reprezentaci s plovoucí desetinnou čárkou a zaokrouhlení.

## <a name="syntax"></a>Syntaxe

```cpp
#include <limits>

```

## <a name="remarks"></a>Poznámky

Explicitní specializace `numeric_limits` třídy popisují mnoho vlastností ze základní typy, včetně znaku, celé číslo a typy s plovoucí desetinnou čárkou a **bool** , které jsou implementace definované, spíše než opravených pravidla jazyka C++. Vlastnosti podle \<omezení > zahrnout přesnost, minimální a maximální velikosti reprezentace, zaokrouhlení a signalizace chyby typu.

### <a name="enumerations"></a>Výčty

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|Výčet popisuje různé metody, které můžete vybrat implementaci představující hodnotu s plovoucí desetinnou čárkou Nenormalizovaná – jeden příliš malá, aby reprezentovala normalizovanou hodnotu:|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|Výčet popisuje různé metody, které můžete vybrat implementaci při zaokrouhlení s plovoucí desetinnou čárkou na celočíselnou hodnotu.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[numeric_limits – třída](../standard-library/numeric-limits-class.md)|Třída šablony popisuje aritmetické vlastnosti předdefinovaných číselných typů.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
