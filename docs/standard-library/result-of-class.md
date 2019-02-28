---
title: result_of – třída
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
ms.openlocfilehash: f60a3ef6528da33fd1117fc940e961e9fe0987df
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006549"
---
# <a name="resultof-class"></a>result_of – třída

Určuje návratový typ volatelného typu, který přijímá zadanými typy argumentu. Přidáno v C ++ 14, zastaralé v C ++ 17.

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

*Fn*<br/>
Volatelný typ dotazu.

*ArgTypes*<br/>
Typy seznamu argumentů na volatelný typ dotazu.

## <a name="remarks"></a>Poznámky

Pomocí této šablony můžete určit výsledný typ v době kompilace `Fn`(`ArgTypes`), kde *Fn* je volatelný typ, odkaz na funkci nebo odkaz na volatelný typ vyvolán pomocí seznam argumentů typů v  *ArgTypes*. `type` Názvy výsledný typ členů třídy šablony `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` Pokud nevyhodnoceném výrazu `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` ve správném formátu. V opačném případě šablony třídy nemá žádný člen `type`. Typ *Fn* a všechny typy v balíček parametrů *ArgTypes* musí být kompletními typy **void**, nebo pole s neznámým rozsahem. Nepoužívané nahrazený [invoke_result](invoke-result-class.md) v C ++ 17.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[Třída invoke_result](invoke-result-class.md)<br/>
