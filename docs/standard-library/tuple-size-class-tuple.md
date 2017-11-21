---
title: "tuple_size – třída; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
dev_langs: C++
helpviewer_keywords: std::tuple_size
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bd57cd0e0c66340eabd54c41c24d892fe9a23bec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tuplesize-class"></a>tuple_size – třída;
Sestavy počet prvků který `tuple` obsahuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
// TEMPLATE STRUCT tuple_size  
template <class Tuple>  
   struct tuple_size;  
  
// number of elements in array  
template <class Elem, size_t Size>  
   struct tuple_size<array<Elem, Size>>  
      : integral_constant<size_t, Size>; 
  
// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>> 
      : integral_constant<size_t, 2>

// size of tuple  
template <class... Types>  
   struct tuple_size<tuple<Types...>>  
      : integral_constant<size_t, sizeof...(Types)>;  
  
// size of const tuple  
template <class Tuple>  
   struct tuple_size<const Tuple>;  
  
// size of volatile tuple  
template <class Tuple>  
   struct tuple_size<volatile Tuple>;  
  
// size of const volatile tuple  
template <class Tuple>  
   struct tuple_size<const volatile Tuple>;   
```  
  
#### <a name="parameters"></a>Parametry  
*Řazené kolekce členů*  
Typ řazenou kolekci členů. 
  
*Elem*  
Typ elementů pole. 
  
*Velikost*  
Velikost pole. 
  
*T1*  
Typ prvního člena, které odpovídá páru. 
  
*T2*  
Typ druhý člen, které odpovídá páru. 
  
*Typy*  
Typy elementů řazené kolekce členů. 
  
  
## <a name="remarks"></a>Poznámky  
Šablony třídy obsahuje člena `value` tedy celočíselné konstantní výraz jehož hodnota je v rozsahu typu řazené kolekce členů `Tuple`.  
  
Specializace šablony pro pole obsahuje člena `value` tedy celočíselné konstantní výraz jehož hodnota je `Size`, což je velikost pole.  
  
Specializace šablony pro dvojici obsahuje člena `value` tedy celočíselné konstantní výraz jehož hodnota je 2.  
  
## <a name="example"></a>Příklad  
  
```cpp  
#include <tuple>   
#include <iostream>  
  
using namespace std;  
  
typedef tuple<int, double, int, double> MyTuple;  
int main()  
{  
    MyTuple c0(0, 1.5, 2, 3.7);  
  
    // display contents " 0 1 2 3"   
    cout << " " << get<0>(c0);  
    cout << " " << get<1>(c0);  
    cout << " " << get<2>(c0);  
    cout << " " << get<3>(c0) << endl;  
  
    // display size " 4"   
    cout << " " << tuple_size<MyTuple>::value << endl;  
}  
```  
  
```Output  
 0 1.5 2 3.7  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<řazené kolekce členů >  
 **Záhlaví:** \<pole > (pro specializaci pole)  
 **Záhlaví:** \<nástroj > (pro dvojice specializace)  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [\<řazené kolekce členů >](../standard-library/tuple.md)   
 [řazené kolekce členů](../standard-library/tuple-class.md)  
 [tuple_element – třída](../standard-library/tuple-element-class-tuple.md)
