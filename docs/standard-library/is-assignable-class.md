---
title: is_assignable třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e8ee756ce98e1476f10c04c10da1c6bce486513
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
