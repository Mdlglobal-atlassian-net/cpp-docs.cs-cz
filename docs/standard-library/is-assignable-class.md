---
title: is_assignable třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd8b757ab46d462bd5d6a596f7dbbfdd18061a8d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="isassignable-class"></a>is_assignable – třída

Kontroluje, zda hodnota `From` typ lze přiřadit k `To` typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

Typ objektu, který obdrží přiřazení.

Z typu objektu, který obsahuje hodnotu.

## <a name="remarks"></a>Poznámky

Unevaluated výraz `declval<To>() = declval<From>()` musí být ve správném formátu. Obě `From` a `To` musí být úplný typy `void`, nebo pole neznámé hranice.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
