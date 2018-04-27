---
title: less_equal – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xfunctional/std::less_equal
dev_langs:
- C++
helpviewer_keywords:
- less_equal function
- less_equal struct
ms.assetid: 32085782-c7e0-4310-9b40-8aa3c1bff211
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f0854aa712a5a3bef6667a09a9b5daf35c52e46b
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="lessequal-struct"></a>less_equal – struktura

Predikát binární, který provede operaci menší než nebo rovno ( `operator<=`) na její argumenty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type = void>
struct less_equal : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<=
template <>
struct less_equal<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    -> decltype(std::forward<T>(Left) <= std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

`Type`, `T`, `U` Žádný typ, který podporuje `operator<=` , která má operandy zadán nebo odvozené typy.

`Left` Levý operand operace menší než nebo rovno. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `T`.

`Right` Pravý operand operace menší než nebo rovno. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `U`.

## <a name="return-value"></a>Návratová hodnota

Výsledek `Left <= Right`. Specializované šablony ideální předávání výsledku, který má typ vrácený `operator<=`.

## <a name="remarks"></a>Poznámky

Binární predikát `less_equal` <  `Type`> poskytuje striktní slabé řazení sady hodnot element typu `Type` do třídy ekvivalenční jenom v případě tohoto typu splňuje požadavky na standardní matematické pro proto řazen. Specializací pro jakýkoli typ ukazatele yield celkový řazení elementů v tom, že všechny elementy odlišné hodnoty jsou seřazené s ohledem na sebe navzájem.

## <a name="example"></a>Příklad

```cpp
// functional_less_equal.cpp
// compile with: /EHsc
#define _CRT_RAND_S
#include <stdlib.h>
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
   vector <int>::reverse_iterator rIter1;
   unsigned int randomNumber;

   int i;
   for ( i = 0 ; i < 5 ; i++ )
   {
      if ( rand_s( &randomNumber ) == 0 )
      {
         // Convert the random number to be between 1 - 50000
         // This is done for readability purposes
         randomNumber = ( unsigned int) ((double)randomNumber /
            (double) UINT_MAX * 50000) + 1;

         v1.push_back( randomNumber );
      }
   }
   for ( i = 0 ; i < 3 ; i++ )
   {
      v1.push_back( 2836 );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use the binary predicate less_equal<int>( )
   sort( v1.begin( ), v1.end( ), less_equal<int>( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

## <a name="sample-output"></a>Vzorový výstup

```Output
Original vector v1 = (31247 37154 48755 15251 6205 2836 2836 2836)
Sorted vector v1 = (2836 2836 2836 6205 15251 31247 37154 48755)
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
