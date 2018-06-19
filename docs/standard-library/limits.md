---
title: '&lt;omezení&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- limits/std::<limits>
- <limits>
dev_langs:
- C++
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a3250d9a090dcbd5eaa9a3cc0d51df84600ed3e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912872"
---
# <a name="ltlimitsgt"></a>&lt;Omezení&gt;

Definuje třídu šablony `numeric_limits` a dva výčty týkající se reprezentace plovoucí desetinné čárky a zaokrouhlení.

## <a name="syntax"></a>Syntaxe

```cpp
#include <limits>

```

## <a name="remarks"></a>Poznámky

Explicitní specializací `numeric_limits` třída popisují mnoho vlastností základních typů, včetně znaku, celé číslo a typy s plovoucí desetinnou čárkou a `bool` , které jsou implementace definované než Pevná pravidly C++ jazyk. Vlastnosti popsané v \<omezení > zahrnují přesnost, minimální a maximální velikost reprezentace zaokrouhlení a signalizace typ chyby.

### <a name="enumerations"></a>Výčty

|||
|-|-|
|[float_denorm_style –](../standard-library/limits-enums.md#float_denorm_style)|Výčet popisuje různé metody, které můžete vybrat implementace pro představující hodnotu s plovoucí desetinnou čárkou nenormalizované – jeden příliš malá, aby představují jako normalizovanou hodnotu:|
|[float_round_style –](../standard-library/limits-enums.md#float_round_style)|Výčet popisuje různé metody, které můžete vybrat implementace pro zaokrouhlení hodnotu s plovoucí desetinnou čárkou na celočíselnou hodnotu.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[numeric_limits – třída](../standard-library/numeric-limits-class.md)|Šablony třídy popisuje aritmetické vlastnosti vestavěné číselné typy.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
