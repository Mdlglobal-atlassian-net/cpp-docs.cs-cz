---
title: is_nothrow_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: 7ec4fc3ef5d9a799d5d77124870fbb337061c94c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455996"
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible – třída

Testuje, zda je typ constructible a že je známo, že se má vyvolávat při použití zadaných typů argumentů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

*Argumentů*\
Typy argumentů, které se mají spárovat v konstruktoru *T*.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud je typ *T* constructible pomocí typů *argumentů v*argumentech a konstruktor je znám kompilátorem, který není vyvolán; v opačném případě obsahuje hodnotu NEPRAVDA. Typ *T* je constructible v případě, že `T t(std::declval<Args>()...);` definice proměnné je ve správném formátu. *T* i všechny typy v argumentech *argumentů* musí být úplné typy, **void**nebo pole neznámého typu Bound.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
