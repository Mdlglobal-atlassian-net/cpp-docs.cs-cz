---
title: is_nothrow_assignable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_assignable
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
ms.openlocfilehash: 9ee8b5f97c92b6eb378db40f93696e5e6c554205
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456024"
---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable – třída

Testuje, zda lze přiřadit hodnotu *z* typu *k typu a* přiřazení je známo, že není vyvolána.

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>Parametry

*Schopn*\
Typ objektu, který přijímá přiřazení.

*Výsledkem*\
Typ objektu, který poskytuje hodnotu.

## <a name="remarks"></a>Poznámky

Výraz `declval<To>() = declval<From>()` musí být ve správném formátu a musí být známý kompilátorem, který nelze vyvolat. *Mezi* i *pro* musí být úplné typy, **void**nebo pole neznámého typu Bound.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
