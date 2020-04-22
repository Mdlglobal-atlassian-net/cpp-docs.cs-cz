---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 60ad1c1bd95eb35f2a4f2800f79d0326c68a1176
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745845"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Specifické pro Microsoft**

Přiřadí tomuto `_variant_t` objektu řetězec.

## <a name="syntax"></a>Syntaxe

```cpp
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parametry

*pSrc*<br/>
Ukazatel na řetězec znaků.

## <a name="remarks"></a>Poznámky

Převede řetězec znaků standardu ANSI na řetězec `BSTR` znakové sady Unicode a přiřadí jej tomuto objektu `_variant_t`.

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[_variant_t – třída](../cpp/variant-t-class.md)
