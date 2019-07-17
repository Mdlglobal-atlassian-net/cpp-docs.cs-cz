---
title: greater_equal – struktura
ms.date: 11/04/2016
f1_keywords:
- functional/std::greater_equal
helpviewer_keywords:
- greater_equal struct
- greater_equal function
ms.assetid: a8ba911b-7af8-4653-b972-d8618f4df7d5
ms.openlocfilehash: f09364203c905407d8ce4607f527d58108eec778
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243746"
---
# <a name="greaterequal-struct"></a>greater_equal – struktura

Binární predikát, který provádí operace větší než nebo rovno (`operator>=`) na svých argumentů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type = void>
struct greater_equal : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator>=
template <>
struct greater_equal<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left)>= std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

*Typ*, *T*, *U*\
Libovolný typ, který podporuje `operator>=` , která přebírá operandů zadaný nebo odvozené typy.

*doleva*\
Levý operand operace větší než nebo rovno. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *T*.

*doprava*\
Pravý operand operace větší než nebo rovno. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *U*.

## <a name="return-value"></a>Návratová hodnota

Výsledek `Left >= Right`. Specializovaná šablona perfektní přesměrování výsledku, který má typ, který je vrácen `operator>=`.

## <a name="remarks"></a>Poznámky

Binární predikát `greater_equal` < `Type`> poskytuje přísné slabé seřazení sady hodnot prvků typu *typ* na rovnocennost třídy pouze v případě tento typ splňuje standard matematické požadavky na seřadí se tak. Specializace pro libovolný typ ukazatele yield celkového pořadí prvků, v tom, že všechny prvky různých hodnot jsou uspořádány ve vztahu mezi sebou.

## <a name="example"></a>Příklad

```cpp
// functional_greater_equal.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   v1.push_back( 6262 );
   v1.push_back( 6262 );
   for ( i = 0 ; i < 5 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // specify binary predicate greater_equal<int>( )
   sort( v1.begin( ), v1.end( ), greater_equal<int>( ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (6262 6262 41 18467 6334 26500 19169)
Sorted vector v1 = (41 6262 6262 6334 18467 19169 26500)
Resorted vector v1 = (26500 19169 18467 6334 6262 6262 41)
```
