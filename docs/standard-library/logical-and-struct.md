---
title: logical_and – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::logical_and
dev_langs:
- C++
helpviewer_keywords:
- logical_and class
- logical_and struct
ms.assetid: 1a375cc2-0592-4d57-a553-78009c7ad610
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cab2335a8e9adb3e4f68f8576df466be45f01504
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100790"
---
# <a name="logicaland-struct"></a>logical_and – struktura

Předdefinovaný objekt funkce, který provádí operace logického spojení (`operator&&`) na svých argumentů.

## <a name="syntax"></a>Syntaxe

```
template <class Type = void>
struct logical_and : public binary_function<Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator&&
template <>
struct logical_and<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) && std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

*Typ*, *T*, *U* libovolný typ, který podporuje `operator&&` , která přebírá operandů zadaný nebo odvozené typy.

*doleva*<br/>
Levý operand operace logického spojení. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *T*.

*doprava*<br/>
Pravý operand operace logického spojení. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *U*.

## <a name="return-value"></a>Návratová hodnota

Výsledek `Left && Right`. Specializovaná šablona perfektní přesměrování výsledku, který má typ, který je vrácen `operator&&`.

## <a name="remarks"></a>Poznámky

Pro typy definované uživatelem neexistuje žádné krátký cyklus vyhodnocení operand. Oba argumenty jsou vyhodnocovány pomocí `operator&&`.

## <a name="example"></a>Příklad

```cpp
// functional_logical_and.cpp
// compile with: /EHsc

#define _CRT_RAND_S
#include <stdlib.h>
#include <deque>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   deque<bool> d1, d2, d3( 7 );
   deque<bool>::iterator iter1, iter2, iter3;

   unsigned int randomValue;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
   {
      if ( rand_s( &randomValue ) == 0 )
      {
         d1.push_back((bool)(( randomValue % 2 ) != 0));
      }

   }

   int j;
   for ( j = 0 ; j < 7 ; j++ )
   {
      if ( rand_s( &randomValue ) == 0 )
      {
         d2.push_back((bool)(( randomValue % 2 ) != 0));
      }
   }

   cout << boolalpha;    // boolalpha I/O flag on

   cout << "Original deque:\n d1 = ( " ;
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )
      cout << *iter1 << " ";
   cout << ")" << endl;

   cout << "Original deque:\n d2 = ( " ;
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )
      cout << *iter2 << " ";
   cout << ")" << endl;

   // To find element-wise conjunction of the truth values
   // of d1 & d2, use the logical_and function object
   transform( d1.begin( ), d1.end( ), d2.begin( ),
      d3.begin( ), logical_and<bool>( ) );
   cout << "The deque which is the conjuction of d1 & d2 is:\n d3 = ( " ;
   for ( iter3 = d3.begin( ) ; iter3 != d3.end( ) ; iter3++ )
      cout << *iter3 << " ";
   cout << ")" << endl;
}

/* Output:
Original deque:
d1 = ( true true true true true false false )
Original deque:
d2 = ( true false true true false true false )
The deque which is the conjuction of d1 & d2 is:
d3 = ( true false true true false false false )
*/
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
