---
title: is_destructible třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- type_traits/std::is_destructible
dev_langs:
- C++
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 887946156084d962debf569fc4f23f45dea18293
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
