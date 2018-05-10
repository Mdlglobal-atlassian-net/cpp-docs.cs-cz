---
title: is_destructible třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_destructible
dev_langs:
- C++
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41a5da108c082dc4199a216d36f51d41e1748ada
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="isdestructible-class"></a>is_destructible – třída

Ověřuje, zda je typ zničitelné.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>Parametry

`T` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `T` zničitelné typu, jinak má hodnotu false. Zničitelné typy jsou odkazové typy, kde je pro nějaký typ objektu typy a typy `U` rovna `remove_all_extents_t<T>` unevaluated operand `std::declval<U&>.~U()` je ve správném formátu. Jiné typy, včetně neúplné typy `void`a funkce typy, nejsou zničitelné typy.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
