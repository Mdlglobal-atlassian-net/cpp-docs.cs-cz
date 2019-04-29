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
ms.openlocfilehash: e0d26247868440f47c73422510ac0e998f8e8dee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403292"
---
# <a name="variantt-relational-operators"></a>_variant_t – relační operátory

**Microsoft Specific**

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