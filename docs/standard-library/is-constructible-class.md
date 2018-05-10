---
title: is_constructible třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2461d7986e87bed846d09d6e3938a339237c8f8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="isconstructible-class"></a>is_constructible – třída

Testuje, zda je zkonstruovatelný typu, pokud se používá zadané typy argumentů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>Parametry

`T` Typ k dotazu.

`Args` Typy argumentů tak, aby odpovídaly v konstruktoru objektu `T`.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je zkonstruovatelný pomocí typy argumentů v `Args`, jinak má hodnotu false. Typ `T` je zkonstruovatelný Pokud za definicí proměnné `T t(std::declval<Args>()...);` je ve správném formátu. Obě `T` a všechny typy v `Args` musí být úplný typy `void`, nebo pole neznámé hranice.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
