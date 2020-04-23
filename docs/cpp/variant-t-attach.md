---
title: _variant_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
ms.openlocfilehash: d0822dfc730cbbb64f8364e6fa8fe8bc7207f9f9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750740"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Specifické pro Microsoft**

Připojí `VARIANT` objekt k **_variant_t** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Parametry

*varSrc*<br/>
Objekt, `VARIANT` který má být připojen k tomuto **_variant_t** objektu.

## <a name="remarks"></a>Poznámky

Přebírá vlastnictví `VARIANT` tím, že zapouzdření to. Tato členská funkce uvolní všechny `VARIANT`existující zapouzdřené , pak zkopíruje zadaný `VARIANT`a nastaví jeho `VARTYPE` VT_EMPTY, aby se ujistil, že jeho prostředky mohou být uvolněny pouze **_variant_t** destruktoru.

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[_variant_t – třída](../cpp/variant-t-class.md)
