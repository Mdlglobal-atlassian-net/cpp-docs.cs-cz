---
title: is_destructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_destructible
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
ms.openlocfilehash: 1036a3756a736ee3916ed9fca84aa935bb0ba2cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336826"
---
# <a name="isdestructible-class"></a>is_destructible – třída

Ověřuje, zda typ zničitelné.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* zničitelné typ, jinak má hodnotu false. Zničitelné typy jsou typy odkazů, kde pro nějaký typ objektu typy a typy `U` rovna `remove_all_extents_t<T>` nevyhodnoceném operand `std::declval<U&>.~U()` ve správném formátu. Jiné typy, včetně neúplných typů **void**a funkce typů, nejsou zničitelné typy.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
