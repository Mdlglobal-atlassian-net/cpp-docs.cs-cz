---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: d07e995be0ecd99974356a7516e7c4deee677637
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403266"
---
# <a name="varianttsetstring"></a>_variant_t::SetString

**Microsoft Specific**

Přiřadí řetězec tomuto `_variant_t` objektu.

## <a name="syntax"></a>Syntaxe

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parametry

*pSrc*<br/>
Ukazatel na řetězec znaků.

## <a name="remarks"></a>Poznámky

Převede řetězec znaků standardu ANSI na řetězec `BSTR` znakové sady Unicode a přiřadí jej tomuto objektu `_variant_t`.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_variant_t – třída](../cpp/variant-t-class.md)