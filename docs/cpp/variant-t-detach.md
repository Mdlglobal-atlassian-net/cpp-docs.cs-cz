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
ms.openlocfilehash: 9737db6b77483fa55e1dad90b9464752cd8537a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187736"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Specifické pro společnost Microsoft**

Odpojí zapouzdřený `VARIANT` objekt od tohoto objektu `_variant_t`.

## <a name="syntax"></a>Syntaxe

```
VARIANT Detach( );
```

## <a name="return-value"></a>Návratová hodnota

Zapouzdřený `VARIANT`.

## <a name="remarks"></a>Poznámky

Extrahuje a vrátí zapouzdřený `VARIANT`a pak vymaže tento objekt `_variant_t` bez zničení. Tato členská funkce odstraní `VARIANT` ze zapouzdření a nastaví `VARTYPE` tohoto objektu `_variant_t` na VT_EMPTY. Je až do uvolnění vrácených `VARIANT` voláním funkce [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_variant_t – třída](../cpp/variant-t-class.md)
