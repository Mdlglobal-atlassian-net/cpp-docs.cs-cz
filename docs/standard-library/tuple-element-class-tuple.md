---
title: "tuple_element – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- utility/std::tuple_element
dev_langs:
- C++
helpviewer_keywords:
- std::tuple_element
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e108f012dbad9e82f85bca08a7e6086734cf001
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="tupleelement-class"></a>tuple_element – třída
Zabalí `tuple` elementu. Zabalení specializací `array` elementy a `pair` elementy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
// CLASS tuple_element (find element by index)  
template <size_t Index, class Tuple>  
   struct tuple_element;  
 
// tuple_element for const 
template <size_t Index, class Tuple>  
   struct tuple_element<Index, const Tuple>;  
 
// tuple_element for volatile  
template <size_t Index, class Tuple>  
   struct tuple_element<Index, volatile Tuple>;  
 
// tuple_element for const volatile  
template <size_t Index, class Tuple>  
   struct tuple_element<Index, const volatile Tuple>;  
 
// Helper typedef
template <size_t Index, class Tuple>  
   using tuple_element_t = typename tuple_element<Index, Tuple>::type; 

// Specialization for arrays  
template <size_t Index, class Elem, size_t Size>  
   struct tuple_element<Index, array<Elem, Size>>;  
  
// Specializations for pairs
// struct to determine type of element 0 in pair
template <class T1, class T2>
   struct tuple_element<0, pair<T1, T2>>;

// struct to determine type of element 1 in pair
template <class T1, class T2>
   struct tuple_element<1, pair<T1, T2>>;
```  
  
### <a name="parameters"></a>Parametry  
*Index*  
Index prvku určené.  
  
*řazené kolekce členů*  
Typ řazenou kolekci členů.  
  
Elem  
Typ pole elementu.  
  
*Velikost*  
Velikost pole.  

*T1* typ prvním elementem v pár.
  
*T2*  
Typ druhého element v pár.

## <a name="remarks"></a>Poznámky  
Šablony třídy `tuple_element` má vnořené typedef `type` tedy synonymum pro typ indexem `Index` typu řazené kolekce členů `Tuple`.  

Typedef `tuple_element_t` je vhodné aliasu pro `tuple_element<Index, Tuple>::type`.  
  
Poskytuje rozhraní pro specializaci třídy šablon pro pole `array` jako řazená kolekce členů `Size` prvky, z nichž každá má stejného typu. Každý specializace má vnořené typedef `type` tedy synonymum pro typ `Index` element `array`, s kvalifikací žádné const volatile zachovaná.  
  
Specializace šablony pro `pair` typy každý zadejte definici typu jednoho člena `type`, což je synonymum pro typ elementu na zadané pozici v páru, s const nebo volatile kvalifikaci, která se zachovají. Typedef `tuple_element_t` je vhodné aliasu pro `tuple_element<N, pair<T1, T2>>::type`.  
  
Použití [get – funkce &lt;nástroj&gt; ](../standard-library/utility-functions.md#get) vrátit element na zadané pozici nebo zadaného typu. 
  
## <a name="example"></a>Příklad  
  
```cpp  
#include <tuple>  
#include <string>  
#include <iostream>  
  
using namespace std;  
typedef tuple<int, double, string> MyTuple;  
  
int main() {  
    MyTuple c0{ 0, 1.5, "Tail" };  
  
    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index  
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);  
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type  
  
    cout << val << " " << val2 << " " << val3 << endl;  
}  
```  
  
```Output  
0 1.5 Tail  
```  
  
## <a name="example"></a>Příklad  
  
```cpp  
#include <array>   
#include <iostream>   
  
using namespace std;  
typedef array<int, 4> MyArray;  
  
int main()  
{  
    MyArray c0 { 0, 1, 2, 3 };  
  
    for (const auto& e : c0)  
    {  
        cout << " " << e;  
    }  
    cout << endl;  
  
    // display first element " 0"   
    tuple_element<0, MyArray>::type val = c0.front();  
    cout << " " << val << endl;  
}  
```  
  
```Output  
 0 1 2 3  
 0  
```  
  
## <a name="example"></a>Příklad  
  
```cpp  
#include <utility>   
#include <iostream>   
  
using namespace std;  
  
typedef pair<int, double> MyPair;  
int main() {  
    MyPair c0(0, 1.333);  
  
    // display contents " 0 1"   
    cout << " " << get<0>(c0);  
    cout << " " << get<1>(c0) << endl;  
  
    // display first element " 0" by index  
    tuple_element<0, MyPair>::type val = get<0>(c0);  
    cout << " " << val;  
  
    // display second element by type   
    tuple_element<1, MyPair>::type val2 = get<double>(c0);  
    cout << " " << val2 << endl;  
}  
```  
  
```Output  
 0 1.333  
 0 1.333  
```  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<řazené kolekce členů >  
 **Záhlaví:** \<pole > (pro pole specializace) **záhlaví:** \<nástroj > (pro dvojice specializací) **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
[řazené kolekce členů ](../standard-library/tuple-class.md)
