---
title: is_nothrow_constructible třída | Microsoft Docs
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
- type_traits/std::is_nothrow_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38c334524cc5965f187d5ec76f698e9ed275f8b0
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible – třída

Ověřuje, zda je zkonstruovatelný typu a není znám výjimku, pokud se používá zadané typy argumentů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>Parametry

`T` Typ k dotazu.

`Args` Typy argumentů tak, aby odpovídaly v konstruktoru objektu `T`.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je zkonstruovatelný pomocí typy argumentů v `Args`a konstruktoru není znám kompilátorem throw; jinak má hodnotu false. Typ `T` je zkonstruovatelný Pokud za definicí proměnné `T t(std::declval<Args>()...);` je ve správném formátu. Obě `T` a všechny typy v `Args` musí být úplný typy `void`, nebo pole neznámé hranice.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
