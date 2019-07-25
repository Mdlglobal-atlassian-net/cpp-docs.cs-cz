---
title: '&lt;lhůty&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: de8f815cd59b84a1e63c231e18e4882d0b5d6f09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447575"
---
# <a name="ltlimitsgt"></a>&lt;lhůty&gt;

Definuje třídu `numeric_limits` šablony a dva výčty týkající se reprezentace a zaokrouhlení plovoucí desetinné čárky.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<omezení >

**Obor názvů:** std

## <a name="remarks"></a>Poznámky

Explicitní specializace `numeric_limits` třídy popisují mnoho vlastností základních typů, včetně znaků, čísel a typů s plovoucí desetinnou čárkou a **logické** hodnoty C++jazyk. Vlastnosti popsané v \<omezeních > zahrnují přesnost, minimální a maximální velikost reprezentace, zaokrouhlení a chyby typu signalizace.

## <a name="members"></a>Členové

### <a name="enumerations"></a>Výčty

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|Výčet popisuje různé metody, které může implementace zvolit pro reprezentaci denormalizované hodnoty s plovoucí desetinnou čárkou – jedna je příliš malá, aby byla reprezentována jako normalizovaná hodnota:|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|Výčet popisuje různé metody, které může implementace zvolit pro zaokrouhlování hodnoty s plovoucí desetinnou čárkou na celočíselnou hodnotu.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[numeric_limits – třída](../standard-library/numeric-limits-class.md)|Třída Template popisuje aritmetické vlastnosti předdefinovaných číselných typů.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
