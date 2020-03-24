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
ms.openlocfilehash: b0692c9befaa6b7e787ada624dcbb56b074c9f9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160460"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Specifické pro společnost Microsoft**

Změní typ objektu `_variant_t` na uvedený `VARTYPE`.

## <a name="syntax"></a>Syntaxe

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Parametry

*VARTYPE*<br/>
`VARTYPE` pro tento objekt `_variant_t`

*pSrc*<br/>
Ukazatel na objekt `_variant_t`, který má být převeden. Pokud je tato hodnota NULL, převod je proveden na místě.

## <a name="remarks"></a>Poznámky

Tato členská funkce převede objekt `_variant_t` na uvedený `VARTYPE`. Pokud má *pSrc* hodnotu null, provede se převod na místě, jinak se tento objekt `_variant_t` zkopíruje z *pSrc* a pak se převede.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_variant_t – třída](../cpp/variant-t-class.md)
