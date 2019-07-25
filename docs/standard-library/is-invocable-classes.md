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
ms.openlocfilehash: 20fec55fc3ad1924ee85db3b2f78812e4847f447
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456235"
---
# <a name="isinvocable-isinvocabler-isnothrowinvocable-isnothrowinvocabler-classes"></a>třídy is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r

Tyto šablony určují, zda lze typ vyvolat se zadanými typy argumentů. `is_invocable_r`a `is_nothrow_invocable_r` také určíte, zda je výsledek vyvolání převeden na konkrétní typ. `is_nothrow_invocable`a `is_nothrow_invocable_r` také určete, zda je vyvolání známo, že nevyvolává výjimky. Přidáno v C++ 17.

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

*Kompatibilní*\
Typ, který se má volat pro dotaz

*Argumentů*\
Typy argumentů pro dotazování.

*Cenný*\
Typ, na který se má *volat* , se musí převést na.

## <a name="remarks"></a>Poznámky

Predikát typu má hodnotu true, pokud lze volat *typ Invoke* pomocí argumentů argumenty v nehodnoceném kontextu.  `is_invocable`

Predikát typu má hodnotu true, *Pokud typ možné* volání lze vyvolat pomocí argumentů *argumentů v* nehodnoceném kontextu pro vytvoření typu výsledku převoditelného pro převoditelné.  `is_invocable_r`

Predikát typu má hodnotu true, pokud volaný typ *Invoke lze vyvolat* pomocí argumentů *argumentů v* nehodnoceném kontextu a že takové volání je známo, že nevyvolává výjimku. `is_nothrow_invocable`

Predikát typu má hodnotu true, pokud *volaný typ Invoke* lze vyvolat pomocí argumentů *argumentů v* nehodnoceném kontextu pro vytvoření typu výsledku převoditelného pro převoditelné a že takové volání je známo, že není throw.  `is_nothrow_invocable_r` výjimka.

Každý z typů převoditelné, *volatelné*a typy v argumentech sady *parametrů musí být* úplný typ, pole neznámého objektu Bound nebo pravděpodobně **typ void**, který je typu CV kvalifikován. V opačném případě chování predikátu není definováno.

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

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
