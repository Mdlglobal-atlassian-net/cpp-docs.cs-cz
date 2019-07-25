---
title: is_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: dc0596ac7a3fc2bcbcbe49f5fa4b20a971e5e445
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452865"
---
# <a name="isconstructible-class"></a>is_constructible – třída

Testuje, zda je typ constructible při použití zadaných typů argumentů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

*Argumentů*\
Typy argumentů, které se mají spárovat v konstruktoru *T*.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu *true, pokud*je typ *T* constructible pomocí typů argumentů v argumentech. v opačném případě obsahuje hodnotu false. Typ *T* je constructible v případě, že `T t(std::declval<Args>()...);` definice proměnné je ve správném formátu. *T* i všechny typy v argumentech *argumentů* musí být úplné typy, **void**nebo pole neznámého typu Bound.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
