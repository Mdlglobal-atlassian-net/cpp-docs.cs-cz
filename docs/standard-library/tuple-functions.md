---
title: '&lt;řazené kolekce členů&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- tuple/std::get
- tuple/std::make_tuple
- tuple/std::tie
ms.assetid: bc6be38f-5258-4c14-b81b-63caa335fd44
helpviewer_keywords:
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
ms.openlocfilehash: 93c11a89f7cdfa3949be2d97e401fad199a17d97
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435530"
---
# <a name="lttuplegt-functions"></a>&lt;řazené kolekce členů&gt; funkce

||||
|-|-|-|
|[get](#get)|[make_tuple](#make_tuple)|[Tie](#tie)|

## <a name="get"></a>  získat

Získá prvek z `tuple` objektu pomocí indexu nebo (v C ++ 14) podle typu.

```cpp
// by index:
// get reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>& get(tuple<Types...>& Tuple) noexcept;

// get const reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr const tuple_element_t<Index, tuple<Types...>>& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>&& get(tuple<Types...>&& Tuple) noexcept;

// (C++14) by type:
// get reference to T element of tuple
template <class T, class... Types>
   constexpr T& get(tuple<Types...>& Tuple) noexcept;

// get const reference to T element of tuple
template <class T, class... Types>
   constexpr const T& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to T element of tuple
template <class T, class... Types>
   constexpr T&& get(tuple<Types...>&& Tuple) noexcept;
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Index prvku, který chcete získat.

*Typy*<br/>
Posloupnost typy deklarované v řazené kolekci členů, v pořadí deklarace.

*T*<br/>
Typ elementu, který chcete získat.

*Řazené kolekce členů*<br/>
Std::tuple, která obsahuje libovolný počet prvků.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí odkaz na hodnotu indexu *Index*, nebo typu *T* v `tuple` objektu.

Volání `get<T>(Tuple)` způsobí chybu kompilátoru, pokud řazená kolekce členů obsahuje více nebo méně než jeden element typu T.

### <a name="example"></a>Příklad

```cpp
#include <tuple>
#include <iostream>
#include <string>

using namespace std;

int main() {
    tuple<int, double, string> tup(0, 1.42, "Call me Tuple");

    // get elements by index
    cout << " " << get<0>(tup);
    cout << " " << get<1>(tup);
    cout << " " << get<2>(tup) << endl;

    // get elements by type
    cout << " " << get<int>(tup);
    cout << " " << get<double>(tup);
    cout << " " << get<string>(tup) << endl;
}
```

```Output
0 1.42 Call me Tuple
0 1.42 Call me Tuple
```

## <a name="make_tuple"></a>  make_tuple –

Díky `tuple` z hodnot prvků.

```cpp
template <class T1, class T2, ..., class TN>
   tuple<V1, V2, ..., VN> make_tuple(const T1& t1, const T2& t2, ..., const TN& tN);
```

### <a name="parameters"></a>Parametry

*TN*<br/>
Typ parametru Nth – funkce

*TN*<br/>
Hodnota parametru n-tý funkce.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí `tuple<V1, V2, ..., VN>(t1, t2, ..., tN)`, kde každý typ `Vi` je `X&` při příslušného `Ti` je `cv` `reference_wrapper<X>`; v opačném případě je `Ti`.

Jednou z výhod `make_tuple` je, že typy ukládaných objektů jsou určeny automaticky kompilátorem a není nutné explicitně zadat. Nepoužívejte explicitní argumenty šablony, jako `make_tuple<int, int>(1, 2)` při použití `make_tuple` protože je zbytečně podrobný a přidá komplexní rvalue reference problémy, které mohou způsobit selhání kompilace.

### <a name="example"></a>Příklad

```cpp
// std__tuple__make_tuple.cpp
// compile by using: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    c0 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
```

## <a name="tie"></a>  Tie

Díky `tuple` z elementu odkazů.

```cpp
template <class T1, class T2, ..., class TN>
tuple<T1&, T2&, ..., TN&> tie(T1& t1, T2& t2, ..., TN& tN);
```

### <a name="parameters"></a>Parametry

*TN*<br/>
Základní typ řazené kolekce členů n-tý prvek.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí `tuple<T1&, T2&, ..., TN&>(t1, t2, ..., tN)`.

### <a name="example"></a>Příklad

```cpp
// std__tuple__tie.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    int v4 = 4;
    double v5 = 5;
    int v6 = 6;
    double v7 = 7;
    std::tie(v4, v5, v6, v7) = c0;

// display contents " 0 1 2 3"
    std::cout << " " << v4;
    std::cout << " " << v5;
    std::cout << " " << v6;
    std::cout << " " << v7;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>Viz také:

[\<řazené kolekce členů >](../standard-library/tuple.md)<br/>
