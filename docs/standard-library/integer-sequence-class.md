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
ms.openlocfilehash: d0de2e56e1f6b8e68e5989f21ecd89b9646caa1b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076463"
---
# <a name="integer_sequence-class"></a>integer_sequence – třída

Představuje posloupnost celého čísla. Dá se použít k odvození a rozbalení balíčků parametrů v variadické typech, jako je std:: Tuple\<T... >, které jsou předány jako argumenty funkce.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Parametry

*T*\
Typ hodnot; musí se jednat o celočíselný typ: bool, char, char16_t, char32_t, wchar_t nebo signed nebo unsigned integer Types.

*Vals*\
Sada parametrů bez typu, která představuje sekvenci hodnot integrálního typu T.

## <a name="members"></a>Členové

|||
|-|-|
|`static size_t size() noexcept`|Počet prvků v sekvenci.|
|`typedef T value_type`|Typ každého prvku v sekvenci. Musí být integrálního typu.|

## <a name="remarks"></a>Poznámky

Balíček parametrů, který se předává přímo funkci, můžete rozbalit bez jakýchkoli speciálních pomocníků knihovny. Když je balíček parametrů součástí typu, který je předán funkci, a potřebujete indexy pro přístup k prvkům, pak nejjednodušší způsob, jak ho rozbalit, je použít `integer_sequence` a jeho související aliasy typu `make_integer_sequence`, `index_sequence`, `make_index_sequence`a `index_sequence_for`.

## <a name="example"></a>Příklad

Následující příklad je založen na původním návrhu [N3658](https://wg21.link/n3658). Ukazuje, jak použít `integer_sequence` k vytvoření `std::tuple` z `std::array<T,N>`a o tom, jak použít `integer_sequence` k získání na členy řazené kolekce členů.

Ve funkci `a2t` je `index_sequence` aliasem `integer_sequence` na základě `size_t` integrálního typu. `make_index_sequence` je alias, který v době kompilace vytvoří `index_sequence` na základě nuly se stejným počtem elementů jako pole, které je předáno volajícím. `a2t` předá `index_sequence` hodnotou `a2t_`, kde výraz `a[I]...` rozbalí `I`a pak se tyto prvky dodávají do `make_tuple`, který je spotřebovává jako jednotlivé argumenty. Například pokud sekvence obsahuje tři prvky, pak `make_tuple` je volána jako make_tuple (a [0], [1], a [2]). Prvky pole samotné můžou být samozřejmě libovolný typ.

Funkce Apply akceptuje [std:: Tuple](../standard-library/tuple-class.md)a vytvoří `integer_sequence` pomocí pomocné třídy `tuple_size`. Všimněte si, že [std::d ecay_t](../standard-library/decay-class.md) je nutné, protože [tuple_size](../standard-library/tuple-size-class-tuple.md) nepracuje s odkazovým typem. Funkce `apply_` rozbalí členy řazené kolekce členů a předá je jako samostatné argumenty volání funkce. V tomto příkladu je funkce jednoduchý výraz lambda, který tiskne hodnoty.

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

Chcete-li nastavit `index_sequence` pro sadu parametrů, použijte `index_sequence_for`\<T... >, což je alias pro `make_index_sequence`\<sizeof... (T) >

## <a name="requirements"></a>Požadavky

Záhlaví: \<type_traits\>

Statements: std

## <a name="see-also"></a>Viz také

[Tři tečky a variadické šablony](../cpp/ellipses-and-variadic-templates.md)
