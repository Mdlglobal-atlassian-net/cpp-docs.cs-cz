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
ms.openlocfilehash: c2283158856a6781ab2e12c51f4e2ad0e4f1d531
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750725"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Specifické pro Microsoft**

Změní typ objektu `_variant_t` na uvedený `VARTYPE`.

## <a name="syntax"></a>Syntaxe

```cpp
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Parametry

*vartyp*<br/>
Pro `VARTYPE` tento `_variant_t` objekt.

*pSrc*<br/>
Ukazatel na objekt `_variant_t`, který má být převeden. Pokud je tato hodnota NULL, převod se provádí na místě.

## <a name="remarks"></a>Poznámky

Tato členská funkce `_variant_t` převede objekt `VARTYPE`na indikovaný . Pokud *pSrc* je NULL, převod se provádí `_variant_t` na místě, jinak tento objekt je zkopírován z *pSrc* a pak převedeny.

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[_variant_t – třída](../cpp/variant-t-class.md)
