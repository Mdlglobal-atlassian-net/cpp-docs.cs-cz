---
title: is_trivially_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_constructible
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
ms.openlocfilehash: c83bea8be5c88876ffa25337464caa62b998ab45
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628836"
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible – třída

Ověřuje, zda typ triviálně constructible zadáním zadanými typy argumentu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

*Args*<br/>
Typy argumentů tak, aby odpovídaly v konstruktoru sady *T*.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je triviálně constructible pomocí typy argumentů v *Args*, v opačném případě obsahuje hodnotu false. Typ *T* je triviálně constructible Pokud za definicí proměnné `T t(std::declval<Args>()...);` ve správném formátu a je známa volat žádné netriviální operace. Obě *T* a všechny typy v *Args* musí být kompletními typy **void**, nebo pole s neznámým rozsahem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
