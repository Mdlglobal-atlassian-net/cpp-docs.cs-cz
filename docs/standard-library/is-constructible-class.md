---
title: is_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: c921efd5b7e12873ce986952029ae39f118ad763
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658650"
---
# <a name="isconstructible-class"></a>is_constructible – třída

Ověřuje, zda typ constructible zadáním zadanými typy argumentu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

*Args*<br/>
Typy argumentů tak, aby odpovídaly v konstruktoru sady *T*.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je constructible pomocí typy argumentů v *Args*, v opačném případě obsahuje hodnotu false. Typ *T* je constructible Pokud za definicí proměnné `T t(std::declval<Args>()...);` ve správném formátu. Obě *T* a všechny typy v *Args* musí být kompletními typy **void**, nebo pole s neznámým rozsahem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
