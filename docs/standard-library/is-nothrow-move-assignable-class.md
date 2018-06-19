---
title: is_nothrow_move_assignable třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_move_assignable
ms.assetid: 000baa02-cbba-49de-9870-af730033348e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 311f4f26b1f63c089c1771e36ac70060fab6b894
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852120"
---
# <a name="isnothrowmoveassignable-class"></a>is_nothrow_move_assignable – třída

Kontroluje, zda má typ **nothrow** operátor move assignment.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parametry

`Ty` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` má nothrow přesunutí operátor přiřazení, jinak má hodnotu false.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
