---
title: greater_equal – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::greater_equal
dev_langs:
- C++
helpviewer_keywords:
- greater_equal struct
- greater_equal function
ms.assetid: a8ba911b-7af8-4653-b972-d8618f4df7d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f87ae764372990a96515a73789b373d2d6d7d01
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843415"
---
# <a name="greaterequal-struct"></a>greater_equal – struktura

Predikát binární, který provede operaci větší než nebo rovno ( `operator>=`) na její argumenty.

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

`Type`, `T`, `U` Žádný typ, který podporuje `operator>=` , která má operandy zadán nebo odvozené typy.

`Left` Levý operand operace větší než nebo rovno. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `T`.

`Right` Pravý operand operace větší než nebo rovno. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `U`.

## <a name="return-value"></a>Návratová hodnota

Výsledek `Left >= Right`. Specializované šablony ideální předávání výsledku, který má typ, který je vrácen rutinou `operator>=`.

## <a name="remarks"></a>Poznámky

Binární predikát `greater_equal` <  `Type`> poskytuje striktní slabé řazení sady hodnot element typu `Type` do třídy ekvivalenční jenom v případě tohoto typu splňuje požadavky na standardní matematické pro proto řazen. Specializací pro jakýkoli typ ukazatele yield celkový řazení elementů v tom, že všechny elementy odlišné hodnoty jsou seřazené s ohledem na sebe navzájem.

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

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
