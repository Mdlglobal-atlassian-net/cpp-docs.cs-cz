---
title: "equal_to – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::equal_to
dev_langs: C++
helpviewer_keywords:
- equal_to function
- equal_to struct
ms.assetid: 8e4f2b50-b2db-48e3-b4cc-6cc03362c2a6
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 416b506d9008ef808016322f9d1c548bcec93450
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="equalto-struct"></a>equal_to – struktura
Predikát binární, který provede operaci rovnosti ( `operator==`) na její argumenty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Type = void>  
struct equal_to : public binary_function<Type, Type, bool>   
 {  
    bool operator()(const Type& Left, const Type& Right) const; 
 };  
 
// specialized transparent functor for operator== 
template <>  
struct equal_to<void>  
 {  
    template <class T, class U>  
    auto operator()(T&& Left, U&& Right) const 
      ->  decltype(std::forward<T>(Left) == std::forward<U>(Right));
 };  
```  
  
#### <a name="parameters"></a>Parametry  
 `Type`, `T`, `U`  
 Žádný typ, který podporuje `operator==` , která má operandy zadán nebo odvozené typy.  
  
 `Left`  
 Levý operand operace rovnosti. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `T`.  
  
 `Right`  
 Pravý operand operace rovnosti. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `U`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Výsledek `Left == Right`. Specializované šablony ideální předávání výsledku, který má typ, který je vrácen rutinou `operator==`.  
  
## <a name="remarks"></a>Poznámky  
 Objekty typu `Type` musí být porovnatelný z hlediska rovnosti. To vyžaduje, aby `operator==` definované v matematickém vlastnosti vztahu ekvivalenční splňuje sadu objektů. Všechny předdefinované typy číselné a ukazatel splnění tohoto požadavku.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// functional_equal_to.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <double> v1, v2, v3 ( 6 );  
   vector <double>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i+=2 )  
   {  
      v1.push_back( 2.0 *i );  
      v1.push_back( 2.0 * i + 1.0 );  
   }  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j+=2 )  
   {  
      v2.push_back( - 2.0 * j );  
      v2.push_back( 2.0 * j + 1.0 );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Testing for the element-wise equality between v1 & v2  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),   
      equal_to<double>( ) );  
  
   cout << "The result of the element-wise equal_to comparison\n"  
      << "between v1 & v2 is: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
The vector v1 = ( 0 1 4 5 8 9 )  
The vector v2 = ( -0 1 -4 5 -8 9 )  
The result of the element-wise equal_to comparison  
between v1 & v2 is: ( 1 1 0 1 0 1 )  
```
