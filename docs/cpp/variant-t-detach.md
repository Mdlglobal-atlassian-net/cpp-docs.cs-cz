---
title: _variant_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
ms.openlocfilehash: 719852c4556291747b612d54c44d4bf82caa9188
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165928"
---
# <a name="varianttdetach"></a>_variant_t::Detach

**Microsoft Specific**

Odpojí zapouzdřeného `VARIANT` objektu z tohoto `_variant_t` objektu.

## <a name="syntax"></a>Syntaxe

```
VARIANT Detach( );
```

## <a name="return-value"></a>Návratová hodnota

Zapouzdřený objekt `VARIANT`.

## <a name="remarks"></a>Poznámky

Extrahuje a vrátí zapouzdřený objekt `VARIANT`, následně smaže `_variant_t` objekt bez došlo k jeho zničení. Tato členská funkce odebere `VARIANT` ze zapouzdření a nastaví `VARTYPE` tohoto `_variant_t` objekt VT_EMPTY. Je na vás, abyste uvolnili vrácený `VARIANT` voláním [VariantClear](/windows/desktop/api/oleauto/nf-oleauto-variantclear) funkce.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_variant_t – třída](../cpp/variant-t-class.md)