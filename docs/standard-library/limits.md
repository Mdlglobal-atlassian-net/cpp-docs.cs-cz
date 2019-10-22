---
title: '&lt;limits &gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 3ad740975cfff4f65f9e1c800a709cfaca3367db
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687811"
---
# <a name="ltlimitsgt"></a>&lt;limits &gt;

Definuje šablonu třídy `numeric_limits` a dva výčty týkající se reprezentace a zaokrouhlení s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<limits >

**Obor názvů:** std

## <a name="remarks"></a>Poznámky

Explicitní specializace `numeric_limits` třídy popisují mnoho vlastností základních typů, včetně znaků, čísel a typů s plovoucí desetinnou čárkou a **bool** , která jsou definovaná implementací, místo aby byla opravena pravidly C++ Language. Vlastnosti popsané v \<limits > zahrnují přesnost, minimální a maximální velikost reprezentace, zaokrouhlování a chyby typu signalizace.

## <a name="members"></a>Členové

### <a name="enumerations"></a>Výčty

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|Výčet popisuje různé metody, které může implementace zvolit pro reprezentaci denormalizované hodnoty s plovoucí desetinnou čárkou – jedna je příliš malá, aby byla reprezentována jako normalizovaná hodnota:|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|Výčet popisuje různé metody, které může implementace zvolit pro zaokrouhlování hodnoty s plovoucí desetinnou čárkou na celočíselnou hodnotu.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[numeric_limits – třída](../standard-library/numeric-limits-class.md)|Šablona třídy popisuje aritmetické vlastnosti předdefinovaných číselných typů.|

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
