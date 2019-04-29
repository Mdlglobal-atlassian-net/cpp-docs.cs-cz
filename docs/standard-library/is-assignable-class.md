---
title: is_assignable Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
ms.openlocfilehash: b1357bf8c5ad4dfd5035855e34a8fd6a7ed73d15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391007"
---
# <a name="isassignable-class"></a>is_assignable Class

Testuje, zda je hodnota `From` typ lze přiřadit k `To` typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

*Komu*<br/>
Typ objektu, která obdrží přiřazení.

*z*<br/>
Typ objektu, který obsahuje hodnotu.

## <a name="remarks"></a>Poznámky

Nevyhodnoceném výrazu `declval<To>() = declval<From>()` musí být ve správném formátu. Obě `From` a `To` musí být kompletními typy **void**, nebo pole s neznámým rozsahem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
