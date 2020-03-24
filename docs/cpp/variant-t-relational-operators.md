---
title: _variant_t – relační operátory
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
ms.openlocfilehash: e0d7ea1a0bcaf8329cff0cdfb0c01154f3c5a73b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187567"
---
# <a name="_variant_t-relational-operators"></a>_variant_t – relační operátory

**Specifické pro společnost Microsoft**

Porovná dva objekty `_variant_t` k rovnosti nebo nerovnosti.

## <a name="syntax"></a>Syntaxe

```
bool operator==(
   const VARIANT& varSrc) const;
bool operator==(
   const VARIANT* pSrc) const;
bool operator!=(
   const VARIANT& varSrc) const;
bool operator!=(
   const VARIANT* pSrc) const;
```

#### <a name="parameters"></a>Parametry

*varSrc*<br/>
`VARIANT`, která má být porovnána s objektem `_variant_t`.

*pSrc*<br/>
Ukazatel na `VARIANT`, který má být porovnán s objektem `_variant_t`.

## <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu true** , pokud výsledek porovnávání obsahuje **hodnotu false** , pokud není.

## <a name="remarks"></a>Poznámky

Porovná objekt `_variant_t` s `VARIANT`, testováním rovnosti nebo nerovnosti.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_variant_t – třída](../cpp/variant-t-class.md)
