---
title: is_trivially_assignable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_assignable
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
ms.openlocfilehash: 11aed7fbe2540984d8ed69f88b2a95649e8fee70
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457494"
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable – třída

Testuje, zda může být `From` hodnota typu triviálním `To` přiřazená typu

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>Parametry

*Schopn*\
Typ objektu, který přijímá přiřazení.

*Výsledkem*\
Typ objektu, který poskytuje hodnotu.

## <a name="remarks"></a>Poznámky

Výraz `declval<To>() = declval<From>()` musí být ve správném formátu a musí být známý kompilátorem, aby nevyžadoval žádné operace bez triviálních operací. Oba `From` a`To` musí být úplnými typy, **void**nebo poli neznámých vazeb.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
