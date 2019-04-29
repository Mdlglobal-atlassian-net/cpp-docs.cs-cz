---
title: integer_sequence – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
ms.openlocfilehash: c996fdc2756ee489dc3b0abf9321a1d9ce47aded
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404946"
---
# <a name="integersequence-class"></a>integer_sequence – třída

Představuje celé číslo sekvence. Je možné odvodit a rozšiřovat sadami parametrů v variadické typy, jako jsou std::tuple\<T... >, které jsou předávány jako argumenty funkce.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typy hodnot; musí být celočíselného typu: bool, char, char16_t, char32_t, wchar_t, nebo podepsaný nebo nepodepsaný řetězec typy celých čísel.

*Prů*<br/>
Sada parametrů bez typu, který představuje sekvenci hodnot celočíselného typu T.

## <a name="members"></a>Členové

|||
|-|-|
|`static size_t size() noexcept`|Počet prvků v sekvenci.|
|`typedef T value_type`|Typ jednotlivých prvků v sekvenci. Musí být celočíselného typu.|

## <a name="remarks"></a>Poznámky

Sada parametrů, která je předána přímo na funkci může být rozbalené bez jakékoli speciální knihovny pomocné rutiny. Pokud sada parametrů je součástí typu, který je předán do funkce, a potřebujete indexy, které se přistupovat k prvkům a pak je nejjednodušší způsob, jak rozbalit ho použít `integer_sequence` a její související typ aliasy `make_integer_sequence`, `index_sequence`, `make_index_sequence`a `index_sequence_for`.

## <a name="example"></a>Příklad

Následující příklad je založen na původní návrh [N3658](http://open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html). Ukazuje, jak používat `integer_sequence` k vytvoření `std::tuple` z `std::array<T,N>`a jak pomocí `integer_sequence` zobrazíte na členy řazené kolekce členů.

V `a2t` funkce, `index_sequence` je alias pro `integer_sequence` na základě `size_t` celočíselného typu. `make_index_sequence` je alias, který v době kompilace vytvoří nulovým základem `index_sequence` stejný počet elementů jako pole, které je předáno volajícím. `a2t` předává `index_sequence` podle hodnoty do `a2t_` , kde výraz `a[I]...` rozbalí `I`, a pak se se elementy zobrazí `make_tuple` které spotřebovává, je jako jednotlivé argumenty. Například, pokud pořadí obsahuje tři prvky, pak `make_tuple` je volána jako make_tuple – ([0], [1]; a[2]). Prvky pole, sami samozřejmě může být libovolného typu.

Použít funkce přijme [std::tuple](../standard-library/tuple-class.md)a vytvoří se soubor `integer_sequence` pomocí `tuple_size` pomocná třída. Všimněte si, že [std::decay_t](../standard-library/decay-class.md) je nezbytné, protože [tuple_size –](../standard-library/tuple-size-class-tuple.md) nefunguje s typy odkazů. `apply_` Funkce rozbalí členy řazené kolekce členů a předává je jako samostatné argumenty pro volání funkce. V tomto příkladu je funkce jednoduché lambda výraz, který vytiskne hodnoty.

```cpp
#include <stddef.h>
#include <iostream>
#include <tuple>
#include <utility>
#include <array>
#include <string>

using namespace std;

// Create a tuple from the array and the index_sequence
template<typename Array, size_t... I>
auto a2t_(const Array& a, index_sequence<I...>)
{
    return make_tuple(a[I]...);
}

// Create an index sequence for the array, and pass it to the
// implementation function a2t_
template<typename T, size_t N>
auto a2t(const array<T, N>& a)
{
    return a2t_(a, make_index_sequence<N>());
}

// Call function F with the tuple members as separate arguments.
template<typename F, typename Tuple = tuple<T...>, size_t... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return forward<F>(f)(get<I>(forward<Tuple>(args))...);
}

// Create an index_sequence for the tuple, and pass it with the
// function object and the tuple to the implementation function apply_
template<typename F, typename Tuple = tuple<T...>>
decltype(auto) apply(F&& f, Tuple&& args)
{
    using Indices = make_index_sequence<tuple_size<decay_t<Tuple>>::value >;
    return apply_(forward<F>(f), forward<Tuple>(args), Indices());
}

int main()
{
    const array<string, 3> arr { "Hello", "from", "C++14" };

    //Create a tuple given a array
    auto tup = a2t(arr);

    // Extract the tuple elements
    apply([](const string& a, const string& b, const string& c) {cout << a << " " << b << " " << c << endl; }, tup);

    char c;
    cin >> c;
}
```

Chcete-li `index_sequence` sadu parametrů, použijte `index_sequence_for` \<T... > což je alias pro `make_index_sequence` \<sizeof... (T) >

## <a name="requirements"></a>Požadavky

Záhlaví: \<type_traits\>

Obor názvů: std

## <a name="see-also"></a>Viz také:

[Tři tečky a variadické šablony](../cpp/ellipses-and-variadic-templates.md)<br/>
