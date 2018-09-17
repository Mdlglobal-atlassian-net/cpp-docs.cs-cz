---
title: is_trivially_assignable – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd0a8bbffd3a6e0f03635b659dd3743e12c9f077
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700762"
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable – třída

Testuje, zda je hodnota `From` typ lze snadno přiřadit `To` typu

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>Parametry

*k*<br/>
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
