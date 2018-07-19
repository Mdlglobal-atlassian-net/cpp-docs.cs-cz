---
title: is_constructible – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 8f9e3f71a0d8647000f77863ecc9243b069f0521
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955824"
---
# <a name="isconstructible-class"></a>is_constructible – třída

Ověřuje, zda typ constructible zadáním zadanými typy argumentu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>Parametry

*T* typ dotazu.

*Args* typy argumentů tak, aby odpovídaly v konstruktoru sady *T*.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je constructible pomocí typy argumentů v *Args*, v opačném případě obsahuje hodnotu false. Typ *T* je constructible Pokud za definicí proměnné `T t(std::declval<Args>()...);` ve správném formátu. Obě *T* a všechny typy v *Args* musí být kompletními typy **void**, nebo pole s neznámým rozsahem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
