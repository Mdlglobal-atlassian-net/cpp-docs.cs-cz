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
ms.openlocfilehash: 3de64f7855b5158f1565580d305e2a6eeaf3e76f
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031469"
---
# <a name="integer_sequence-class"></a>integer_sequence – třída

Představuje sekvenci celého čísla. Lze použít k odvodit a rozbalit balíčky parametrů v variadických typech, jako je std::n-tple\<T...>, které jsou předány jako argumenty funkci.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Parametry

*T*\
Typ hodnot; musí být integrální typ: bool, char, char16_t, char32_t, wchar_t nebo podepsané nebo nepodepsané typy celého čísla.

*Vals*\
Netypový balíček parametrů, který představuje posloupnost hodnot integrálního typu T.

## <a name="members"></a>Členové

|||
|-|-|
|`static size_t size() noexcept`|Počet prvků v pořadí.|
|`typedef T value_type`|Typ každého prvku v sekvenci. Musí být integrální typ.|

## <a name="remarks"></a>Poznámky

Balíček parametrů, který je předán přímo funkci, lze rozbalit bez zvláštních pomocníků knihovny. Pokud je balíček parametrů součástí typu, který je předán funkci, a potřebujete indexy pro přístup k prvkům, `integer_sequence` je nejjednodušším `make_integer_sequence`způsobem, jak jej rozbalit, a jeho souvisejícím aliasům typu , `index_sequence` `make_index_sequence`, a `index_sequence_for`.

## <a name="example"></a>Příklad

Následující příklad vychází z původního návrhu [N3658](https://wg21.link/n3658). Ukazuje, jak použít `integer_sequence` a `std::tuple` vytvořit `std::array<T,N>`z , a `integer_sequence` jak použít získat na členy řazené kolekce členů.

Ve `a2t` funkci `index_sequence` je alias `integer_sequence` založený na `size_t` integrálním typu. `make_index_sequence`je alias, který v době kompilace vytvoří nulu `index_sequence` se stejným počtem prvků jako pole, které je předáno volajícím. `a2t`předává `index_sequence` hodnotu `a2t_` podle na `a[I]...` , `I`kde se výraz rozbalí `make_tuple` , a potom jsou prvky přiváděny, které je pohlcují jako jednotlivé argumenty. Například pokud sekvence obsahuje tři `make_tuple` prvky, pak se nazývá jako make_tuple(a[0], a[1], a[2]). Samotné prvky pole mohou být samozřejmě libovolným typem.

Funkce apply přijímá [std::n-tice](../standard-library/tuple-class.md)a `integer_sequence` vytváří pomocí `tuple_size` pomocné třídy. Všimněte si, že [std::decay_t](../standard-library/decay-class.md) je [nezbytné,](../standard-library/tuple-size-class-tuple.md) protože tuple_size nefunguje s typy odkazů. Funkce `apply_` rozbalí členy řazené kolekce členů a předá je jako samostatné argumenty volání funkce. V tomto příkladu je funkce jednoduchý lambda výraz, který vytiskne hodnoty.

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

Chcete-li `index_sequence` vytvořit pro balíček parametrů, použijte `index_sequence_for` \<T...> což je alias pro `make_index_sequence` \<sizeof... (T)>

## <a name="requirements"></a>Požadavky

Záhlaví: \<type_traits\>

Namepace: std

## <a name="see-also"></a>Viz také

[Tři tečky a variadické šablony](../cpp/ellipses-and-variadic-templates.md)
