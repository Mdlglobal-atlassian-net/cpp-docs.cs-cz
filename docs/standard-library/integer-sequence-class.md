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
ms.openlocfilehash: ca923933ac7a401f6a3ef14f821ceb04b844797b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451010"
---
# <a name="integersequence-class"></a>integer_sequence – třída

Představuje posloupnost celého čísla. Dá se použít k odvození a rozbalení balíčků parametrů v variadické typech, jako je std:\<: Tuple T... >, které jsou předány jako argumenty funkce.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Parametry

*Š*\
Typ hodnot; musí být celočíselný typ: bool, char, char16_t, char32_t, wchar_t nebo signed nebo unsigned integer Types.

*Vals*\
Sada parametrů bez typu, která představuje sekvenci hodnot integrálního typu T.

## <a name="members"></a>Členové

|||
|-|-|
|`static size_t size() noexcept`|Počet prvků v sekvenci.|
|`typedef T value_type`|Typ každého prvku v sekvenci. Musí být integrálního typu.|

## <a name="remarks"></a>Poznámky

Balíček parametrů, který se předává přímo funkci, můžete rozbalit bez jakýchkoli speciálních pomocníků knihovny. Pokud je balíček parametrů součástí typu, který je předán funkci, a potřebujete indexy pro přístup k prvkům, pak nejjednodušší způsob, jak ho rozbalit, je `integer_sequence` použít a jeho související aliasy `make_integer_sequence`typu, `index_sequence` `make_index_sequence`, a `index_sequence_for`.

## <a name="example"></a>Příklad

Následující příklad je založen na původním návrhu [N3658](http://open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html). Ukazuje `integer_sequence` `std::array<T,N>`, jak použít k `std::tuple` vytvoření z a, jak použít `integer_sequence` k získání na členy řazené kolekce členů.

`a2t` Ve funkci `index_sequence` je alias`integer_sequence`na základě integrálníhotypu.`size_t` `make_index_sequence`je alias, který v době kompilace vytvoří nulu `index_sequence` se stejným počtem elementů jako pole, které je předáno volajícím. `a2t``make_tuple` `I` `a[I]...` předá `index_sequence` `a2t_` hodnotu podle, kde se výraz rozbalí, a poté jsou předávány elementy, které je používají jako jednotlivé argumenty. Například pokud sekvence obsahuje tři prvky, pak `make_tuple` je volána jako make_tuple (a [0], a [1], a [2]). Prvky pole samotné můžou být samozřejmě libovolný typ.

Funkce Apply akceptuje [std:: Tuple](../standard-library/tuple-class.md)a vytvoří `integer_sequence` pomocí `tuple_size` pomocné třídy. Všimněte si, že [std::d ecay_t](../standard-library/decay-class.md) je nezbytné, protože [tuple_size](../standard-library/tuple-size-class-tuple.md) nepracuje s odkazovým typem. `apply_` Funkce rozbalí členy řazené kolekce členů a předá je jako samostatné argumenty volání funkce. V tomto příkladu je funkce jednoduchý výraz lambda, který tiskne hodnoty.

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

Chcete-li `index_sequence` vytvořit balíček parametrů, použijte `index_sequence_for` \<T... >, což je alias pro `make_index_sequence` \<operátor sizeof... (T) >

## <a name="requirements"></a>Požadavky

Záhlaví: \<type_traits\>

Statements: std

## <a name="see-also"></a>Viz také:

[Tři tečky a variadické šablony](../cpp/ellipses-and-variadic-templates.md)
