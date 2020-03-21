---
title: třídy is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::is_invocable
- type_traits/std::is_invocable_r
- type_traits/std::is_nothrow_invocable
- type_traits/std::is_nothrow_invocable_r
helpviewer_keywords:
- is_invocable class
- is_invocable
- is_invocable_r class
- is_invocable_r
- is_nothrow_invocable class
- is_nothrow_invocable
- is_nothrow_invocable_r class
- is_nothrow_invocable_r
ms.openlocfilehash: 53394a10464e2688953cd1b5703530e2719b7593
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076455"
---
# <a name="is_invocable-is_invocable_r-is_nothrow_invocable-is_nothrow_invocable_r-classes"></a>třídy is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r

Tyto šablony určují, zda lze typ vyvolat se zadanými typy argumentů. `is_invocable_r` a `is_nothrow_invocable_r` také určí, zda je výsledek vyvolání převeden na konkrétní typ. `is_nothrow_invocable` a `is_nothrow_invocable_r` také určit, zda vyvolání není známo, že vyvolává výjimky. Přidáno v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Callable, class... Args>
struct is_invocable;

template <class Convertible, class Callable, class... Args>
struct is_invocable_r;

template <class Callable, class... Args>
struct is_nothrow_invocable;

template <class Convertible, class Callable, class... Args>
struct is_nothrow_invocable_r;

// Helper templates
template <class Callable, class... Args>
inline constexpr bool is_invocable_v =
    std::is_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_invocable_r_v =
    std::is_invocable_r<Convertible, Callable, Args...>::value;

template <class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_v =
    std::is_nothrow_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_r_v =
    std::is_nothrow_invocable_r<Convertible, Callable, Args...>::value;
```

### <a name="parameters"></a>Parametry

*Volat*\
Typ, který se má volat pro dotaz

\ *argumentů*
Typy argumentů pro dotazování.

*Převoditelné*\
Typ, na který se má *volat* , se musí převést na.

## <a name="remarks"></a>Poznámky

Predikát `is_invocable`ho typu má hodnotu true, pokud lze *volat typ Invoke* *pomocí argumentů argumenty v* nehodnoceném kontextu.

Predikát `is_invocable_r`ho typu má hodnotu true, pokud volaný typ, který lze *volat* , lze vyvolat *pomocí argumentů argumentů v* nehodnoceném kontextu pro vytvoření typu výsledku převoditelného na *převoditelný*.

Predikát `is_nothrow_invocable`ho typu má hodnotu true, pokud volaný *typ Invoke* lze vyvolat *pomocí argumentů argumentů v* nehodnoceném kontextu a že takové volání je známo, že nevyvolává výjimku.

Predikát `is_nothrow_invocable_r`ho typu má hodnotu true, pokud lze *volat typ,* který lze vyvolat pomocí *argumentů argumentů v* nehodnoceném kontextu pro vytvoření typu výsledku převoditelného pro *převoditelné*a že takové volání je známo, že nevyvolá výjimku.

Každý z typů *převoditelné*, *volatelné*a typy v argumentech sady *parametrů musí být* úplný typ, pole neznámého objektu Bound nebo pravděpodobně **typ void**, který je typu CV kvalifikován. V opačném případě chování predikátu není definováno.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__is_invocable.cpp
// compile using: cl /EHsc /std:c++17 std__type_traits__is_invocable.cpp
#include <type_traits>

auto test1(int) noexcept -> int (*)()
{
    return nullptr;
}

auto test2(int) -> int (*)()
{
    return nullptr;
}

int main()
{
    static_assert( std::is_invocable<decltype(test1), short>::value );

    static_assert( std::is_invocable_r<int(*)(), decltype(test1), int>::value );
    static_assert( std::is_invocable_r<long(*)(), decltype(test1), int>::value ); // fails

    static_assert( std::is_nothrow_invocable<decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable<decltype(test2), int>::value ); // fails

    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test2), int>::value ); // fails
}
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také

[< type_traits >](../standard-library/type-traits.md)\
[Zavolejte](functional-functions.md#invoke)
