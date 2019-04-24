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
ms.openlocfilehash: 510267c7ab00fe22a93dc01342def5fc262ddb04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166215"
---
# <a name="varianttattach"></a>_variant_t::Attach

**Microsoft Specific**

Připojí `VARIANT` objektu do **_variant_t** objektu.

## <a name="syntax"></a>Syntaxe

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Parametry

*varSrc*<br/>
A `VARIANT` objektu, který chcete připojit k tomuto **_variant_t** objektu.

## <a name="remarks"></a>Poznámky

Převezme vlastnictví `VARIANT` zapouzdřením ho. Tato členská funkce uvolní všechny existující zapouzdřené `VARIANT`, pak zkopíruje zadané `VARIANT`a nastaví její `VARTYPE` VT_EMPTY Ujistěte se, že její prostředky lze pouze budou vydány **_variant_t** destruktor.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_variant_t – třída](../cpp/variant-t-class.md)