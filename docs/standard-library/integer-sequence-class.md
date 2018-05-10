---
title: integer_sequence – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
dev_langs:
- C++
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58700d1f52189afb1d8baf3456bac4ed84920fab
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="integersequence-class"></a>integer_sequence – třída

Představuje v sekvenci celé číslo. Lze odvodit a rozbalte sady parametrů v variadická typy například std::tuple\<T... > které jsou předávány jako argumenty funkce.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Parametry

T typ hodnoty; musí být typu integrální: bool, char, char16_t, char32_t, wchar_t, nebo podepsané nebo typy celé číslo bez znaménka.

Pack Prů A jiný typ parametru, která představuje pořadí hodnot integrální typu T.

## <a name="members"></a>Členové

|||
|-|-|
|`static size_t size() noexcept`|Počet elementů v pořadí.|
|value_type – TypeDef T|Typ každý prvek v pořadí. Musí být celočíselné typu.|

## <a name="remarks"></a>Poznámky

Parametr pack, která je přímo předaný funkci může být rozbalené bez jakékoli speciální knihovny pomocné rutiny. Když parametr pack je součástí typ, který je předaný funkci, a potřebujete indexy, které se přístup k prvkům a pak je nejjednodušší způsob, jak rozbalit ho používat `integer_sequence` a jeho souvisejících typ aliasy `make_integer_sequence`, `index_sequence`, `make_index_sequence`a `index_sequence_for`.

## <a name="example"></a>Příklad

V následujícím příkladu je založena na původní návrhu [N3658](http://open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html). Ukazuje, jak používat `integer_sequence` k vytvoření `std::tuple` z `std::array<T,N>`a jak používat `integer_sequence` získat na členy řazené kolekce členů.

V `a2t` funkce, `index_sequence` je zástupce `integer_sequence` na základě `size_t` integrální typu. `make_index_sequence` je alias, který v době kompilace vytvoří nulovým základem `index_sequence` s stejný počet elementů jako pole, je předaná volající funkcí. `a2t` předá `index_sequence` hodnotou k `a2t_` , kde výraz `a[I]...` rozbalí `I`, a pak se právě elementy dodáni do `make_tuple` což spotřebuje, je jako samostatné argumenty. Například pokud pořadí obsahuje tři prvky, pak `make_tuple` nazývá jako make_tuple – ([0], [1], a[2]). Elementy pole sami samozřejmě mohou být jakéhokoli typu.

Použít funkce přijme [std::tuple](../standard-library/tuple-class.md)a vytvoří integer_sequence pomocí `tuple_size` pomocná třída. Všimněte si, že [std::decay_t](../standard-library/decay-class.md)_is nezbytné protože [tuple_size](../standard-library/tuple-size-class-tuple.md) nefunguje s odkazové typy. `apply_` Funkce rozbalí členy řazené kolekce členů a předává je jako samostatné argumenty pro volání funkce. V tomto příkladu je funkce jednoduché lambda výraz, který vytiskne hodnoty.

```

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

Chcete-li `index_sequence` pro sadu parametrů, použijte `index_sequence_for` \<T... > tedy alias `make_index_sequence` \<sizeof... (T) >

## <a name="requirements"></a>Požadavky

Záhlaví: < type_traits >

Oboru názvů: – std

## <a name="see-also"></a>Viz také

[Tři tečky a variadické šablony](../cpp/ellipses-and-variadic-templates.md)<br/>
