---
title: is_destructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_destructible
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
ms.openlocfilehash: 80592a6fca274533a798b2f5a2459d336ee2c301
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452735"
---
# <a name="isdestructible-class"></a>is_destructible – třída

Testuje, zda je typ zničitelné.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud typ *T* je zničitelné typ, v opačném případě obsahuje hodnotu false. Typy zničitelné jsou odkazové typy, typy objektů a typy, kde pro nějaký `U` typ je `remove_all_extents_t<T>` stejný jako vyhodnocený operand `std::declval<U&>.~U()` je ve správném formátu. Jiné typy, včetně neúplných typů, **void**a typů funkcí, nejsou zničitelné typy.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
