---
title: multiplies – struktura
ms.date: 11/04/2016
f1_keywords:
- functional/std::multiplies
helpviewer_keywords:
- multiplies class
- multiplies struct
ms.assetid: ec85e8af-70ad-44ad-90f0-d961a5847864
ms.openlocfilehash: 7e91c834d3e56d4c0170c4e2f6b26b73dc925432
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186072"
---
# <a name="multiplies-struct"></a>multiplies – struktura

Předdefinovaný objekt funkce, který provádí operace násobení (binární `operator*`) na svých argumentů.

## <a name="syntax"></a>Syntaxe

```
template <class Type = void>
struct multiplies : public binary_function <Type, Type, Type>
{
    Type operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator*
template <>
struct multiplies<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) * std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

*Typ*, *T*, *U* typ, který podporuje binární soubor `operator*` , která přebírá operandů zadaný nebo odvozené typy.

*doleva*<br/>
Levý operand operace násobení. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *T*.

*doprava*<br/>
Pravý operand operace násobení. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *U*.

## <a name="return-value"></a>Návratová hodnota

Výsledek `Left * Right`. Specializovaná šablona perfektní přesměrování výsledku, který má typ, který je vrácen `operator*`.

## <a name="example"></a>Příklad

```cpp
// functional_multiplies.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main( )
{
   vector <int> v1, v2, v3 ( 6 );
   vector <int>::iterator Iter1, Iter2, Iter3;

   int i;
   for ( i = 1 ; i <= 6 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   int j;
   for ( j = 1 ; j <= 6 ; j++ )
   {
      v2.push_back( 3 * j );
   }

   cout << "The vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "The vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Finding the element-wise products of the elements of v1 & v2
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),
      multiplies<int>( ) );

   cout << "The element-wise products of vectors V1 & v2\n are: ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
/* Output:
The vector v1 = ( 2 4 6 8 10 12 )
The vector v2 = ( 3 6 9 12 15 18 )
The element-wise products of vectors V1 & v2
are: ( 6 24 54 96 150 216 )
*/
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
