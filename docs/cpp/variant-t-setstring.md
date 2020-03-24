---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 0cd300a09c29668c496d93109d1bc862947e948c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187554"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Specifické pro společnost Microsoft**

Přiřadí k tomuto objektu `_variant_t` řetězec.

## <a name="syntax"></a>Syntaxe

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parametry

*pSrc*<br/>
Ukazatel na řetězec znaků.

## <a name="remarks"></a>Poznámky

Převede řetězec znaků standardu ANSI na řetězec `BSTR` znakové sady Unicode a přiřadí jej tomuto objektu `_variant_t`.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_variant_t – třída](../cpp/variant-t-class.md)
