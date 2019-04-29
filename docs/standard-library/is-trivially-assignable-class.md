---
title: is_trivially_assignable Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_assignable
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
ms.openlocfilehash: eeef85a0b26c25eb745258c7e0e35394f0cab979
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413488"
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable Class

Testuje, zda je hodnota `From` typ lze snadno přiřadit `To` typu

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>Parametry

*Komu*<br/>
Typ objektu, která obdrží přiřazení.

*z*<br/>
Typ objektu, který obsahuje hodnotu.

## <a name="remarks"></a>Poznámky

Výraz `declval<To>() = declval<From>()` musí být ve správném formátu a musí být pro kompilátor známým tak, aby vyžadovala žádné netriviální operace. Obě `From` a `To` musí být kompletními typy **void**, nebo pole s neznámým rozsahem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
