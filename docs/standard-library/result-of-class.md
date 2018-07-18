---
title: result_of – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
dev_langs:
- C++
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b385d822c2f58d26938b3300207a790dc1193060
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953020"
---
# <a name="resultof-class"></a>result_of – třída

Určuje návratový typ volatelného typu, který přijímá zadanými typy argumentu.

## <a name="syntax"></a>Syntaxe

```cpp
template<class>
struct result_of; // Causes a static assert

template <class Fn, class... ArgTypes>
struct result_of<Fn(ArgTypes...)>;

// Helper type
template<class T>
   using result_of_t = typename result_of<T>::type;
```

### <a name="parameters"></a>Parametry

*Fn* volatelný typ dotazu.

*ArgTypes* typy seznamu argumentů na volatelný typ dotazu.

## <a name="remarks"></a>Poznámky

Pomocí této šablony můžete určit výsledný typ v době kompilace `Fn`(`ArgTypes`), kde *Fn* je volatelný typ, odkaz na funkci nebo odkaz na volatelný typ vyvolán pomocí seznam argumentů typů v  *ArgTypes*. `type` Názvy výsledný typ členů třídy šablony `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` Pokud nevyhodnoceném výrazu `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` ve správném formátu. V opačném případě šablony třídy nemá žádný člen `type`. Typ *Fn* a všechny typy v balíček parametrů *ArgTypes* musí být kompletními typy **void**, nebo pole s neznámým rozsahem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
