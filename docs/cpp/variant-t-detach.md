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
ms.openlocfilehash: 8426c80af04b2c0906af150ea3e91304335e9f69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500561"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Specifické pro společnost Microsoft**

Odpojí zapouzdřený `VARIANT` objekt od tohoto `_variant_t` objektu.

## <a name="syntax"></a>Syntaxe

```
VARIANT Detach( );
```

## <a name="return-value"></a>Návratová hodnota

Zapouzdřený `VARIANT`.

## <a name="remarks"></a>Poznámky

Extrahuje a vrátí zapouzdřený `VARIANT`objekt a odstraní ho bez `_variant_t` zničení tohoto objektu. Tato členská funkce odebere `VARIANT` z zapouzdření a `VARTYPE` nastaví `_variant_t` objekt na VT_EMPTY. Je až do uvolnění vrácené `VARIANT` voláním funkce [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[_variant_t – třída](../cpp/variant-t-class.md)