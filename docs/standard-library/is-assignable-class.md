---
title: is_assignable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
ms.openlocfilehash: 33b0ce6112119c935ff70e5d619b284acc6ee8c2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456671"
---
# <a name="isassignable-class"></a>is_assignable – třída

Testuje, zda může být `From` hodnota typu přiřazena `To` typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

*Schopn*\
Typ objektu, který přijímá přiřazení.

*Výsledkem*\
Typ objektu, který poskytuje hodnotu.

## <a name="remarks"></a>Poznámky

Vyhodnocený výraz `declval<To>() = declval<From>()` musí být ve správném formátu. Oba `From` a`To` musí být úplnými typy, **void**nebo poli neznámých vazeb.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
