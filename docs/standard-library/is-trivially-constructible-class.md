---
title: is_trivially_constructible třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 757a5eb526bc8d4294a64cbdc9645e72285162ce
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible – třída

Ověřuje, zda typ je trivially zkonstruovatelný, pokud se používá zadané typy argumentů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parametry

`T` Typ k dotazu.

`Args` Typy argumentů tak, aby odpovídaly v konstruktoru objektu `T`.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je trivially zkonstruovatelný pomocí typy argumentů v `Args`, jinak má hodnotu false. Typ `T` je trivially zkonstruovatelný Pokud za definicí proměnné `T t(std::declval<Args>()...);` má správný tvar a je zřejmé, že volání žádné netriviální operací. Obě `T` a všechny typy v `Args` musí být úplný typy `void`, nebo pole neznámé hranice.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
