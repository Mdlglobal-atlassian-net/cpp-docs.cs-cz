---
title: tuple – třída
ms.date: 11/04/2016
f1_keywords:
- tuple/std::tuple
- tuple/std::tuple::operator=
helpviewer_keywords:
- tuple class
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
ms.openlocfilehash: 1727d3a12b7186d3cc868ef6bb78711774057407
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688867"
---
# <a name="tuple-class"></a>tuple – třída

Zabalí posloupnost prvků s pevnou délkou.

## <a name="syntax"></a>Syntaxe

```
class tuple {
   tuple();
   explicit tuple(P1, P2, ..., PN); // 0 < N
   tuple(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple(const pair<U1, U2>&); // N == 2

   void swap(tuple& right);
   tuple& operator=(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple& operator=(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple& operator=(const pair<U1, U2>&); // N == 2
};
```

### <a name="parameters"></a>Parametry

@No__t_1 *TN*
Typ n-tý prvek řazené kolekce členů.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který ukládá N objektů typů `T1`, `T2`,... `TN`, v uvedeném pořadí, kde `0 <= N <= Nmax`. Rozsah instance řazené kolekce členů `tuple<T1, T2, ..., TN>` je číslo `N` svých argumentů šablony. Index argumentu šablony `Ti` a odpovídající uložená hodnota tohoto typu je `i - 1`. Proto v této dokumentaci čísly od 1 do N připravujeme hodnoty indexu v rozsahu od 0 do N-1.

## <a name="example"></a>Příklad

```cpp
// tuple.cpp
// compile with: /EHsc

#include <vector>
#include <iomanip>
#include <iostream>
#include <tuple>
#include <string>

using namespace std;

typedef tuple <int, double, string> ids;

void print_ids(const ids& i)
{
   cout << "( "
        << get<0>(i) << ", "
        << get<1>(i) << ", "
        << get<2>(i) << " )." << endl;
}

int main( )
{
   // Using the constructor to declare and initialize a tuple
   ids p1(10, 1.1e-2, "one");

   // Compare using the helper function to declare and initialize a tuple
   ids p2;
   p2 = make_tuple(10, 2.22e-1, "two");

   // Making a copy of a tuple
   ids p3(p1);

   cout.precision(3);
   cout << "The tuple p1 is: ( ";
   print_ids(p1);
   cout << "The tuple p2 is: ( ";
   print_ids(p2);
   cout << "The tuple p3 is: ( ";
   print_ids(p3);

   vector<ids> v;

   v.push_back(p1);
   v.push_back(p2);
   v.push_back(make_tuple(3, 3.3e-2, "three"));

   cout << "The tuples in the vector are" << endl;
   for(vector<ids>::const_iterator i = v.begin(); i != v.end(); ++i)
   {
      print_ids(*i);
   }
}
```

```Output
The tuple p1 is: ( 10, 0.011, one ).
The tuple p2 is: ( 10, 0.222, two ).
The tuple p3 is: ( 10, 0.011, one ).
The tuples in the vector are
( 10, 0.011, one ).
( 10, 0.222, two ).
( 3, 0.033, three ).
```

## <a name="op_eq"></a>operátor =

Přiřadí objekt `tuple`.

```cpp
tuple& operator=(const tuple& right);

template <class U1, class U2, ..., class UN>
   tuple& operator=(const tuple<U1, U2, ..., UN>& right);

template <class U1, class U2>
   tuple& operator=(const pair<U1, U2>& right); // N == 2

tuple& operator=(tuple&& right);

template <class U1, class U2>
   tuple& operator=(pair<U1, U2>&& right);
```

### <a name="parameters"></a>Parametry

*Zrušit* \
Typ n-tý zkopírovaný element řazené kolekce členů.

*pravé* \
Řazená kolekce členů ke zkopírování.

### <a name="remarks"></a>Poznámky

První dva členské operátory přiřadí prvky *vpravo* k odpovídajícím prvkům `*this`. Třetí členský operátor přiřadí `right.first` k elementu na indexu 0 v `*this` a `right.second` prvku na indexu 1. Všechny tři členské operátory vracejí `*this`.

Zbývající členské operátory jsou analogické k těm, ale s [referencemi rvalue deklarátor: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

### <a name="example"></a>Příklad

```cpp
// std__tuple__tuple_operator_as.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
    {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c1);
    std::cout << " " << std::get<1>(c1);
    std::cout << " " << std::get<2>(c1);
    std::cout << " " << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2;
    c2 = std::make_pair('x', 4);

// display contents " x 4"
    std::cout << " " << std::get<0>(c2);
    std::cout << " " << std::get<1>(c2);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
x 4
```

## <a name="tuple_swap"></a>adresu

Vyměňuje prvky dvou řazených kolekcí členů.

```cpp
template <class... Types>
   void swap(tuple<Types...&> left, tuple<Types...&> right);
```

### <a name="parameters"></a>Parametry

*levý* \
Řazená kolekce členů, jejíž prvky mají být vyměňovány pomocí *práv*řazené kolekce členů.

*pravé* \
Řazená kolekce členů, jejíž prvky mají být vyměněny pomocí těch řazené kolekce členů *doleva*.

### <a name="remarks"></a>Poznámky

Funkce provádí `left.swap(right)`.

## <a name="tuple"></a>řazené kolekce členů

Vytvoří objekt `tuple`.

```cpp
constexpr tuple();
explicit constexpr tuple(const Types&...);
template <class... UTypes>
   explicit constexpr tuple(UTypes&&...);

tuple(const tuple&) = default;
tuple(tuple&&) = default;

template <class... UTypes>
   constexpr tuple(const tuple<UTypes...>&);
template <class... UTypes>
   constexpr tuple(tuple<UTypes...>&&);

// only if sizeof...(Types) == 2
template <class U1, class U2>
   constexpr tuple(const pair<U1, U2>&);
template <class U1, class U2>
   constexpr tuple(pair<U1, U2>&&);
```

### <a name="parameters"></a>Parametry

*Zrušit* \
Typ n-tý zkopírovaný element řazené kolekce členů.

*pravé* \
Řazená kolekce členů ke zkopírování.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt, jehož prvky jsou vytvořeny jako výchozí.

Druhý konstruktor vytvoří objekt, jehož prvky jsou zkopírovány z argumentů `P1`, `P2`,... `PN` s každým `Pi` inicializací elementu v indexu `i - 1`.

Třetí a čtvrtý konstruktor vytvoří objekt, jehož prvky jsou zkopírovány z odpovídajícího prvku *Right*.

Pátý konstruktor vytvoří objekt, jehož element na indexu 0 je kopií vytvořenou z `right.first` a jehož element na indexu 1 je kopie vytvořená z `right.second`.

Zbývající konstruktory jsou analogické na dřívější, ale s [odkazem rvalue deklarátor: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

### <a name="example"></a>Příklad

```cpp
// std__tuple__tuple_tuple.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
{
    Mytuple c0(0, 1, 2, 3);

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c1) << " ";
    std::cout << std::get<1>(c1) << " ";
    std::cout << std::get<2>(c1) << " ";
    std::cout << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2(std::make_pair('x', 4));

    // display contents "x 4"
    std::cout << std::get<0>(c2) << " ";
    std::cout << std::get<1>(c2);
    std::cout << std::endl;

    Mytuple c3(c0);

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c3) << " ";
    std::cout << std::get<1>(c3) << " ";
    std::cout << std::get<2>(c3) << " ";
    std::cout << std::get<3>(c3);
    std::cout << std::endl;

    typedef std::tuple<int, float, int, float> Mytuple2;
    Mytuple c4(Mytuple2(4, 5, 6, 7));

    // display contents "4 5 6 7"
    std::cout << std::get<0>(c4) << " ";
    std::cout << std::get<1>(c4) << " ";
    std::cout << std::get<2>(c4) << " ";
    std::cout << std::get<3>(c4);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
x 4
0 1 2 3
4 5 6 7
```
