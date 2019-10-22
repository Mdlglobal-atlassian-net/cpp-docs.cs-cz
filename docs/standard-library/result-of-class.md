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
ms.openlocfilehash: ab575ac31936e7003f19fc2ceb3c5b1727d0728c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689000"
---
# <a name="result_of-class"></a>result_of – třída

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

*Fn* \
Typ, který se má volat pro dotaz

*ArgTypes* \
Typy seznamu argumentů pro dotaz na typ, který se má volat

## <a name="remarks"></a>Poznámky

Tuto šablonu použijte k určení v době kompilace typ výsledku `Fn` (`ArgTypes`), kde *FN* je typ, který lze volat, odkaz na funkci nebo odkaz na typ volat, vyvolán pomocí seznamu argumentů typů v *ArgTypes*. @No__t_0 člen šablony třídy pojmenuje typ výsledku `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))`, je-li vyhodnocený výraz `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` správně vytvořen. V opačném případě šablona třídy nemá žádné členy `type`. Typ *FN* a všechny typy v sadě parametrů *ArgTypes* musí být úplné typy, **void**nebo pole neznámého typu Bound. Zastaralé namísto [invoke_result](invoke-result-class.md) v c++ 17.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md) \
[invoke_result – třída](invoke-result-class.md)
