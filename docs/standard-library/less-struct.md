---
title: less – struktura
ms.date: 11/04/2016
f1_keywords:
- functional/std::less
helpviewer_keywords:
- less struct
- less function
ms.assetid: 39349da3-11cd-4774-b2cc-b46af5aae5d7
ms.openlocfilehash: 13aef35856066f9c1897c3d8855c5ff537aa3567
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245339"
---
# <a name="less-struct"></a>less – struktura

Binární predikát, který provádí méně – než operace (`operator<`) na svých argumentů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type = void>
struct less : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<
template <>
struct less<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) <std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

*Typ*, *T*, *U*\
Libovolný typ, který podporuje `operator<` , která přebírá operandů zadaný nebo odvozené typy.

*doleva*\
Levý operand větší-než operace. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *T*.

*doprava*\
Pravý operand větší-než operace. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *U*.

## <a name="return-value"></a>Návratová hodnota

Výsledek `Left < Right`. Specializovaná šablona perfektní přesměrování výsledku, který má typ, který je vrácen `operator<`.

## <a name="remarks"></a>Poznámky

Binární predikát `less` < `Type`> poskytuje přísné slabé seřazení sady hodnot prvků typu *typ* na rovnocennost třídy pouze v případě tento typ splňuje standard matematické požadavky na seřadí se tak. Specializace pro libovolný typ ukazatele yield celkového pořadí prvků, v tom, že všechny prvky různých hodnot jsou uspořádány ve vztahu mezi sebou.

## <a name="example"></a>Příklad

```cpp
// functional_less.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

struct MyStruct {
   MyStruct(int i) : m_i(i){}

   bool operator < (const MyStruct & rhs) const {
      return m_i < rhs.m_i;
   }

   int m_i;
};

int main() {
   using namespace std;
   vector <MyStruct> v1;
   vector <MyStruct>::iterator Iter1;
   vector <MyStruct>::reverse_iterator rIter1;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
       v1.push_back( MyStruct(rand()));

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )
cout << Iter1->m_i << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   sort( v1.begin( ), v1.end( ), less<MyStruct>());

   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )
cout << Iter1->m_i << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (41 18467 6334 26500 19169 15724 11478)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500)
```
