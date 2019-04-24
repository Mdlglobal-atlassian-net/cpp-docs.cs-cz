---
title: _variant_t::ChangeType
ms.date: 11/04/2016
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
ms.openlocfilehash: 319c4fde808932e86021ee59b051261c43ca2edd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166201"
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType

**Microsoft Specific**

Typ se změní `_variant_t` objekt označený `VARTYPE`.

## <a name="syntax"></a>Syntaxe

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Parametry

*vartype*<br/>
`VARTYPE` To `_variant_t` objektu.

*pSrc*<br/>
Ukazatel na objekt `_variant_t`, který má být převeden. Pokud je tato hodnota NULL, převod se provádí na místě.

## <a name="remarks"></a>Poznámky

Tato členská funkce převede `_variant_t` na zadaný objekt `VARTYPE`. Pokud *pSrc* má hodnotu NULL, převod se provede na místě, jinak to `_variant_t` objekt zkopírován z *pSrc* a poté převeden.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_variant_t – třída](../cpp/variant-t-class.md)