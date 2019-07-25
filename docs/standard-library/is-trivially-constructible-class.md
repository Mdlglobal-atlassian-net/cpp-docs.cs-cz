---
title: is_trivially_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_constructible
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
ms.openlocfilehash: 6f177463b985d3e7b2f7ab7783f9c3db0dcd5722
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448017"
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible – třída

Testuje, zda je typ triviální constructible při použití zadaných typů argumentů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

*Argumentů*\
Typy argumentů, které se mají spárovat v konstruktoru *T*.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu *true, pokud*je typ *T* triviální constructible pomocí typů argumentů v argumentech. v opačném případě obsahuje hodnotu false. Typ *T* je triviální constructible, pokud je definice `T t(std::declval<Args>()...);` proměnné ve správném formátu a je známo, že volá žádné operace, které nejsou triviální. *T* i všechny typy v argumentech *argumentů* musí být úplné typy, **void**nebo pole neznámého typu Bound.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
