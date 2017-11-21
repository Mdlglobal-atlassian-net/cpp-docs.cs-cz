---
title: "Greater – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::greater
dev_langs: C++
helpviewer_keywords:
- greater struct
- greater function
ms.assetid: ebc348e1-edcd-466b-b21a-db95bd8f9079
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 960c8e3f96a79edf8159774e24c1b9744a54cee1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="greater-struct"></a>greater – struktura
Predikát binární, který provádí delší – než operaci ( `operator>`) na její argumenty.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Type = void>
struct greater : public binary_function <Type, Type, bool>  
{
    bool operator()(
    const Type& Left,
    const Type& Right) const;

 };

// specialized transparent functor for operator>
template <>
struct greater<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    ->  decltype(std::forward<T>(Left)> std::forward<U>(Right));
 };
```  
  
#### <a name="parameters"></a>Parametry  
 `Type`, `T`, `U`  
 Žádný typ, který podporuje `operator>` , která má operandy zadán nebo odvozené typy.  
  
 `Left`  
 Levý operand delší – než operaci. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `T`.  
  
 `Right`  
 Pravý operand delší – než operaci. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `U`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Výsledek `Left > Right`. Specializované šablony ideální předávání výsledku, který má typ, který je vrácen rutinou `operator>`.  
  
## <a name="remarks"></a>Poznámky  
 Binární predikát `greater` <  `Type`> poskytuje striktní slabé řazení sady hodnot element typu `Type` do třídy ekvivalenční jenom v případě tohoto typu splňuje požadavky na standardní matematické pro proto řazen. Specializací pro jakýkoli typ ukazatele yield celkový řazení elementů v tom, že všechny elementy odlišné hodnoty jsou seřazené s ohledem na sebe navzájem.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// functional_greater.cpp  
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
   for ( i = 0 ; i < 8 ; i++ )  
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
   // specify binary predicate greater<int>( )  
   sort( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "Resorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
## <a name="output"></a>Výstup  
  
```
Original vector v1 = (41 18467 6334 26500 19169 15724 11478 29358)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500 29358)
Resorted vector v1 = (29358 26500 19169 18467 15724 11478 6334 41)
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<funkční >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)



