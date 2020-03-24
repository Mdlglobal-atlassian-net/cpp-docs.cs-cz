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
ms.openlocfilehash: 3792ed4d0fcd86c4a4e846771c450413fda130b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187762"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Specifické pro společnost Microsoft**

Připojí objekt `VARIANT` k objektu **_variant_t** .

## <a name="syntax"></a>Syntaxe

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Parametry

*varSrc*<br/>
Objekt `VARIANT`, který se má připojit k tomuto objektu **_variant_t** .

## <a name="remarks"></a>Poznámky

Převezme vlastnictví `VARIANT` zapouzdřením. Tato členská funkce uvolní všechny existující zapouzdřené `VARIANT`, zkopíruje dodaný `VARIANT`a nastaví její `VARTYPE` na VT_EMPTY, aby bylo zajištěno, že je možné prostředky uvolnit pouze pomocí **_variant_t** destruktoru.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_variant_t – třída](../cpp/variant-t-class.md)
