---
title: pair – struktura
ms.date: 11/04/2016
f1_keywords:
- utility/std::pair
helpviewer_keywords:
- pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
ms.openlocfilehash: f372ae036ff4843532efa18c3d518820b5f06111
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244421"
---
# <a name="pair-structure"></a>pair – struktura

Struktura, která poskytuje možnost zpracovávat dva objekty jako jednoho objektu.

## <a name="syntax"></a>Syntaxe

```cpp
struct pair
{
    typedef T1 first_type;
    typedef T2 second_type;
    T1 first;
    T2 second;
    constexpr pair();
    pair(const pair&) = default;
    pair(pair&&) = default;
    constexpr pair(
        const T1& Val1,
        const T2& Val2);

    template <class Other1, class Other2>
    constexpr pair(const pair<Other1, Other2>& Right);

    template <class Other1, class Other2>
    constexpr pair(const pair <Other1 Val1, Other2 Val2>&& Right);

    template <class Other1, class Other2>
    constexpr pair(Other1&& Val1, Other2&& Val2);

    template <class... Args1, class... Args2>
    pair(piecewise_construct_t, tuple<Args1...> first_args, tuple<Args2...> second_args);

    pair& operator=(const pair& p);
    template<class U1, class U2> pair& operator=(const pair<U1, U2>& p);
    pair& operator=(pair&& p) noexcept(see below );
    template<class U1, class U2> pair& operator=(pair<U1, U2>&& p);

    void swap(pair& p) noexcept(see below );
};

template<class T1, class T2>
    pair(T1, T2) -> pair<T1, T2>;
```

### <a name="parameters"></a>Parametry

*Val1*\
Hodnota, která inicializuje první prvek `pair`.

*Val2*\
Hodnota, která inicializuje druhý prvek `pair`.

*doprava*\
Dvojice, jejichž hodnoty se mají použít k inicializaci prvků jinou dvojici.

## <a name="return-value"></a>Návratová hodnota

První (výchozí) konstruktor inicializuje první prvek dvojice na výchozí hodnotu typu `T1` a druhý prvek výchozí typ `T2`.

Druhý konstruktor inicializuje první prvek dvojice k *Val1* a druhý k *Val2.*

Třetí konstruktor (šablona) inicializuje první prvek dvojice k `Right`. **první** a druhý k `Right`. **druhý**.

Čtvrtý konstruktor inicializuje první prvek dvojice k *Val1* a druhý k *Val2* pomocí [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="remarks"></a>Poznámky

Šablona struktura ukládá dvojici objektů typu `T1` a `T2`v uvedeném pořadí. Typ `first_type` je stejný jako parametr šablony `T1` a typ `second_type` je stejný jako parametr šablony `T2`. `T1` a `T2` každý potřebovat zadat pouze výchozí konstruktor, jedním argumentem konstruktor a destruktor. Všechny členy typu `pair` jsou veřejné, protože typ je deklarován jako `struct` spíše než stejně jako **třídy**. Tato dvě nejběžnější použití pro pár se jako návratové typy pro funkce, které vrací dvě hodnoty a jako prvky pro třídy asociativní kontejner [map – třída](../standard-library/map-class.md) a [multimap – třída](../standard-library/multimap-class.md) , které mají oba klíče a Typ hodnoty přidružené k každý prvek. Splňuje požadavky kontejner asociativních párů a s typem hodnoty ve formuláři `pair` <  **const**`key_type`, `mapped_type`>.

## <a name="example"></a>Příklad

```cpp
// utility_pair.cpp
// compile with: /EHsc
#include <utility>
#include <map>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;

   // Using the constructor to declare and initialize a pair
   pair <int, double> p1 ( 10, 1.1e-2 );

   // Compare using the helper function to declare and initialize a pair
   pair <int, double> p2;
   p2 = make_pair ( 10, 2.22e-1 );

   // Making a copy of a pair
   pair <int, double> p3 ( p1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;

   // Using a pair for a map element
   map <int, int> m1;
   map <int, int>::iterator m1_Iter;

   typedef pair <int, int> Map_Int_Pair;

   m1.insert ( Map_Int_Pair ( 1, 10 ) );
   m1.insert ( Map_Int_Pair ( 2, 20 ) );
   m1.insert ( Map_Int_Pair ( 3, 30 ) );

   cout << "The element pairs of the map m1 are:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " ( " << m1_Iter -> first << ", "
           << m1_Iter -> second << " )";
   cout   << "." << endl;

   // Using pair as a return type for a function
   pair< map<int,int>::iterator, bool > pr1, pr2;
   pr1 = m1.insert ( Map_Int_Pair ( 4, 40 ) );
   pr2 = m1.insert ( Map_Int_Pair (1, 10 ) );

   if( pr1.second == true )
   {
      cout << "The element (4,40) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr1.first) -> first ) = " << ( pr1.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }

   if( pr2.second == true )
   {
      cout << "The element (1,10) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr2.first) -> first ) = " << ( pr2.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }
}
```

```Output
The pair p1 is: ( 10, 0.011 ).
The pair p2 is: ( 10, 0.222 ).
The pair p3 is: ( 10, 0.011 ).
The element pairs of the map m1 are: ( 1, 10 ) ( 2, 20 ) ( 3, 30 ).
The element (4,40) was inserted successfully in m1.
The element with a key value of
( (pr2.first) -> first ) = 1 is already in m1,
so the insertion failed.
```
