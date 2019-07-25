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
ms.openlocfilehash: 5a3265cfe4b2629bf02925ea6e3eeb0c4acb1e0e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451217"
---
# <a name="resultof-class"></a>result_of – třída

Určuje návratový typ typu volat, který přebírá zadané typy argumentů. Přidáno v C++ 14, zastaralé v C++ 17.

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

*VistaScan*\
Typ, který se má volat pro dotaz

*ArgTypes*\
Typy seznamu argumentů pro dotaz na typ, který se má volat

## <a name="remarks"></a>Poznámky

Pomocí této šablony lze určit v `Fn`době kompilace typ výsledku (`ArgTypes`), kde *FN* je typ, který lze volat, odkaz na funkci nebo odkaz na typ volání, vyvolán pomocí seznamu argumentů typů v *ArgTypes*. Člen třídy šablony pojmenovává `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` typ výsledku, pokud je vyhodnocený výraz `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` správně vytvořen. `type` V opačném případě třída šablony nemá žádné `type`členy. Typ *FN* a všechny typy v sadě parametrů *ArgTypes* musí být úplné typy, **void**nebo pole neznámého typu Bound. Zastaralé namísto [invoke_result](invoke-result-class.md) v c++ 17.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[invoke_result – třída](invoke-result-class.md)
