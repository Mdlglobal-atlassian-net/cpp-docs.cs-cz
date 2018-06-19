---
title: is_nothrow_copy_assignable – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c5c5bdc1e944483071f0f1dcd53c3bc93eb6ed3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842934"
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable – třída

Ověřuje, zda má typ operátor přiřazení kopie, který se označuje kompilátoru nechcete výjimku.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Parametry

`T` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Instance typu predikátu platí pro kde typ `T` kde `is_nothrow_assignable<T&, const T&>` obsahuje hodnotu true; jinak má hodnotu false.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable – třída](../standard-library/is-nothrow-assignable-class.md)<br/>
