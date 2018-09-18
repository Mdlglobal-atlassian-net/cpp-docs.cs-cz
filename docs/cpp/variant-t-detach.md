---
title: _variant_t::detach | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
dev_langs:
- C++
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ab1e4f83025dcc3e4bc65274746e0617cf31b5b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065020"
---
# <a name="varianttdetach"></a>_variant_t::Detach

**Specifické pro Microsoft**

Odpojí zapouzdřeného `VARIANT` objektu z tohoto `_variant_t` objektu.

## <a name="syntax"></a>Syntaxe

```
VARIANT Detach( );
```

## <a name="return-value"></a>Návratová hodnota

Zapouzdřený objekt `VARIANT`.

## <a name="remarks"></a>Poznámky

Extrahuje a vrátí zapouzdřený objekt `VARIANT`, následně smaže `_variant_t` objekt bez došlo k jeho zničení. Tato členská funkce odebere `VARIANT` ze zapouzdření a nastaví `VARTYPE` tohoto `_variant_t` objekt VT_EMPTY. Je na vás, abyste uvolnili vrácený `VARIANT` voláním [VariantClear](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantclear) funkce.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_variant_t – třída](../cpp/variant-t-class.md)