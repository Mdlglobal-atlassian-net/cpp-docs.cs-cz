---
title: _variant_t – relační operátory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95cb1ac663607f26c4f168c2e98910f5b41963c0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040144"
---
# <a name="variantt-relational-operators"></a>_variant_t – relační operátory

**Specifické pro Microsoft**

Porovnat dva `_variant_t` objekty a zjistí rovnost či nerovnost.

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
A `VARIANT` která bude porovnána `_variant_t` objektu.

*pSrc*<br/>
Ukazatel `VARIANT` k porovnání s `_variant_t` objektu.

## <a name="return-value"></a>Návratová hodnota

Vrátí **true** pokud obsahuje porovnání **false** Pokud tomu tak není.

## <a name="remarks"></a>Poznámky

Porovná `_variant_t` objektu `VARIANT`, testování a zjistí rovnost či nerovnost.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_variant_t – třída](../cpp/variant-t-class.md)