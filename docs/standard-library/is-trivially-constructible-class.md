---
title: is_trivially_constructible – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: f73559503ad427c9b7eb513d4164d3348c652948
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954744"
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible – třída

Ověřuje, zda typ triviálně constructible zadáním zadanými typy argumentu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parametry

*T* typ dotazu.

*Args* typy argumentů tak, aby odpovídaly v konstruktoru sady *T*.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je triviálně constructible pomocí typy argumentů v *Args*, v opačném případě obsahuje hodnotu false. Typ *T* je triviálně constructible Pokud za definicí proměnné `T t(std::declval<Args>()...);` ve správném formátu a je známa volat žádné netriviální operace. Obě *T* a všechny typy v *Args* musí být kompletními typy **void**, nebo pole s neznámým rozsahem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
