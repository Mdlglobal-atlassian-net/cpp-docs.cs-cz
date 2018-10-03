---
title: tuple – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- tuple/std::tuple
- tuple/std::tuple::operator=
dev_langs:
- C++
helpviewer_keywords:
- tuple class
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f37a6bdbf35075a9a1a8cea8150e6f8ed85232a5
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234551"
---
# <a name="tuple-class"></a>tuple – třída

Zabalí pevné délky sekvence elementů.

## <a name="syntax"></a>Syntaxe

```
class tuple {
public:
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

*TN*<br/>
Typ prvku n-tý řazené kolekce členů.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který ukládá objekty N typů `T1`, `T2`,..., `TN`v uvedeném pořadí, ve kterém `0 <= N <= Nmax`. Rozsah řazené kolekce členů instance `tuple<T1, T2, ..., TN>` je číslo `N` šablony argumentů. Index argumentu šablony `Ti` a odpovídající uložené hodnotě tohoto typu je `i - 1`. Proto když jsme počet typů od 1 do N v této dokumentaci, odpovídající index hodnoty v rozsahu od 0 do N - 1.

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

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<řazené kolekce členů >

**Namespace:** std

## <a name="op_eq"></a>  tuple::Operator =

Přiřadí `tuple` objektu.

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

*ZRUŠENÍ*<br/>
Typ n-té zkopírovat prvek řazené kolekce členů.

*doprava*<br/>
Kopírování z řazené kolekce členů.

### <a name="remarks"></a>Poznámky

První dvě členské operátory přiřadit elementy *správné* na odpovídající elementy `*this`. Třetí členský operátor přiřadí `right.first` pro element v indexu 0 `*this` a `right.second` na element na indexu 1. Vrátí všechny tři členské operátory `*this`.

Zbývající členské operátory jsou analogických ty dřívější, ale s [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

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

## <a name="tuple_swap"></a>  tuple:swap

Vymění prvky dvou řazené kolekce členů.

```cpp
template <class... Types>
   void swap(tuple<Types...&> left, tuple<Types...&> right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Řazené kolekce členů, jehož prvky mají být zaměněny řazené kolekce členů *správné*.|
|*doprava*|Řazené kolekce členů, jehož prvky mají být zaměněny řazené kolekce členů *levé*.|

### <a name="remarks"></a>Poznámky

Provede se příslušná funkce `left.swap(right)`.

## <a name="tuple"></a>  tuple::tuple

Vytvoří `tuple` objektu.

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

*ZRUŠENÍ*<br/>
Typ n-té zkopírovat prvek řazené kolekce členů.

*doprava*<br/>
Kopírování z řazené kolekce členů.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt, jehož prvky jsou výchozí vyrobený.

Druhý konstruktor vytvoří objekt, jehož prvky jsou kopie vytvořený z argumentů `P1`, `P2`,..., `PN` s každým `Pi` inicializace element v indexu `i - 1`.

Třetí a čtvrtý konstruktor Sestavte objekt, jehož prvky jsou kopie vytvořený z odpovídající prvek *správné*.

Pátý konstruktor zkonstruuje objekt, jehož element na indexu 0 je kopie vytvořený z `right.first` a jejichž element na indexu 1 je kopií vytvořen z `right.second`.

Zbývající konstruktory jsou analogických ty dřívější, ale s [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

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

## <a name="see-also"></a>Viz také:

[\<řazené kolekce členů >](../standard-library/tuple.md)<br/>
[make_tuple](../standard-library/tuple-functions.md#make_tuple)<br/>
