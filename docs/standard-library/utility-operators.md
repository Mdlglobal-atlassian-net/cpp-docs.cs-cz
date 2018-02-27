---
title: "&lt;Nástroj&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- utility/std::operator!=
- utility/std::operator&gt;
- utility/std::operator&gt;=
- utility/std::operator&lt;
- utility/std::operator&lt;=
- utility/std::operator==
dev_langs:
- C++
ms.assetid: a6617109-2cec-4a69-948f-6c87116eda5f
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::operator!= (utility)
- std::operator&gt; (utility)
- std::operator&gt;= (utility)
- std::operator&lt; (utility)
- std::operator&lt;= (utility)
- std::operator== (utility)
ms.openlocfilehash: 407e08934c4469776feb34d0f18b20b457d208d9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltutilitygt-operators"></a>&lt;Nástroj&gt; operátory
||||  
|-|-|-|  
|[operator!=](#op_neq)|[Operátor&gt;](#op_gt)|[Operátor&gt;=](#op_gt_eq)|  
|[Operátor&lt;](#op_lt)|[Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>  Operator! =  
 Testy, pokud objekt dvojice na levé straně operátoru není stejný jako dvojice objekt na pravé straně.  
  
```  
template <class Type>  
constexpr bool operator!=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator!=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **pár.**  
  
 `right`  
 Objekt typu `pair`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud dvojice není stejný; **false** Pokud dvojice jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Jednu dvojici se rovná jinou dvojici, pokud každý z jejich odpovídajících elementů je stejná. Jsou dvě dvojice nerovné, pokud není rovno odpovídající element dvojic první nebo druhý prvkem jednoho.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// utility_op_ne.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 1.11e-1 );  
   p2 = make_pair ( 1000, 1.11e-3 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 != p2 )  
      cout << "The pairs p1 and p2 are not equal." << endl;  
   else  
      cout << "The pairs p1 and p2 are equal." << endl;  
  
   if ( p1 != p3 )  
      cout << "The pairs p1 and p3 are not equal." << endl;  
   else  
      cout << "The pairs p1 and p3 are equal." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.111 ).  
The pair p2 is: ( 1000, 0.00111 ).  
The pair p3 is: ( 10, 0.111 ).  
  
The pairs p1 and p2 are not equal.  
The pairs p1 and p3 are equal.  
```  
  
##  <a name="op_eq_eq"></a>  Operator ==  
 Testy, pokud objekt dvojice na levé straně operátoru rovná objekt dvojice na pravé straně.  
  
```  
template <class T, class U>  
constexpr bool operator==(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **pár.**  
  
 `right`  
 Objekt typu `pair`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud dvojice stejný; **false** Pokud `pair`s nejsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Jednu dvojici se rovná jinou dvojici, pokud každý z jejich odpovídajících elementů je stejná. Funkce vrátí hodnotu `left`. **první** == `right`. **první** && `left`. **druhý** == `right`. **druhý**. Jsou dvě dvojice nerovné, pokud není rovno odpovídající element dvojic první nebo druhý prvkem jednoho.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// utility_op_eq.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 1.11e-1 );  
   p2 = make_pair ( 1000, 1.11e-3 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 == p2 )  
      cout << "The pairs p1 and p2 are equal." << endl;  
   else  
      cout << "The pairs p1 and p2 are not equal." << endl;  
  
   if ( p1 == p3 )  
      cout << "The pairs p1 and p3 are equal." << endl;  
   else  
      cout << "The pairs p1 and p3 are not equal." << endl;  
}  
```  
  
##  <a name="op_lt"></a>  Operátor&lt;  
 Testy, pokud je dvojice objekt na levé straně operátoru je menší než pár objekt na pravé straně.  
  
```  
template <class T, class U>  
constexpr bool operator<(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `pair` na levé straně operátoru.  
  
 `right`  
 Objekt typu `pair` na pravé straně operátoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `pair` na levé straně operátoru je striktně menší než `pair` na pravé straně operátoru; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 `left` `pair` Objektu se říká, že striktně menší než `right` `pair` objektu Pokud `left` je menší než a není rovno `right`.  
  
 Porovnání páry první prvky dvě dvojice hodnot se mají vyšší prioritu. Pokud se liší, je výsledkem porovnávání považován za výsledku porovnání, které odpovídá páru. Pokud nejsou různé hodnoty první elementů, porovnání hodnot druhý elementů a výsledek jejich porovnání se používá jako výsledek porovnání, které odpovídá páru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// utility_op_lt.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 < p2 )  
      cout << "The pair p1 is less than the pair p2." << endl;  
   else  
      cout << "The pair p1 is not less than the pair p2." << endl;  
  
   if ( p1 < p3 )  
      cout << "The pair p1 is less than the pair p3." << endl;  
   else  
      cout << "The pair p1 is not less than the pair p3." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
  
The pair p1 is less than the pair p2.  
The pair p1 is not less than the pair p3.  
```  
  
##  <a name="op_lt_eq"></a>  Operátor&lt;=  
 Testy, pokud je dvojice objekt na levé straně operátoru je menší než nebo rovno objekt dvojice na pravé straně.  
  
```  
template <class Type>  
constexpr bool operator<=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator<=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `pair` na levé straně operátoru.  
  
 `right`  
 Objekt typu `pair` na pravé straně operátoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `pair` na levé straně operátoru je menší než nebo rovno `pair` na pravé straně operátoru; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání páry první prvky dvě dvojice hodnot se mají vyšší prioritu. Pokud se liší, je výsledkem porovnávání považován za výsledku porovnání, které odpovídá páru. Pokud nejsou různé hodnoty první elementů, porovnání hodnot druhý elementů a výsledek jejich porovnání se používá jako výsledek porovnání, které odpovídá páru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// utility_op_le.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 <= p2 )  
      cout << "The pair p1 is less than or equal to the pair p2." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p2." << endl;  
  
   if ( p1 <= p3 )  
      cout << "The pair p1 is less than or equal to the pair p3." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p3." << endl;  
  
   if ( p1 <= p4 )  
      cout << "The pair p1 is less than or equal to the pair p4." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is less than or equal to the pair p2.  
The pair p1 is greater than the pair p3.  
The pair p1 is less than or equal to the pair p4.  
```  
  
##  <a name="op_gt"></a>  Operátor&gt;  
 Testy, pokud objekt dvojice na levé straně operátoru je větší než pár objekt na pravé straně.  
  
```  
template <class Type>  
constexpr bool operator>(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator>(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `pair` na levé straně operátoru.  
  
 `right`  
 Objekt typu `pair` na pravé straně operátoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `pair` na levé straně operátoru je výhradně větší než `pair` na pravé straně operátoru; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 `left` `pair` Objekt se označuje jako být striktně větší než `right` `pair` objektu Pokud `left` je větší než a není rovno `right`.  
  
 Porovnání páry první prvky dvě dvojice hodnot se mají vyšší prioritu. Pokud se liší, je výsledkem porovnávání považován za výsledku porovnání, které odpovídá páru. Pokud nejsou různé hodnoty první elementů, porovnání hodnot druhý elementů a výsledek jejich porovnání se používá jako výsledek porovnání, které odpovídá páru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// utility_op_gt.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 > p2 )  
      cout << "The pair p1 is greater than the pair p2." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p2." << endl;  
  
   if ( p1 > p3 )  
      cout << "The pair p1 is greater than the pair p3." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p3." << endl;  
  
   if ( p1 > p4 )  
      cout << "The pair p1 is greater than the pair p4." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is not greater than the pair p2.  
The pair p1 is greater than the pair p3.  
The pair p1 is not greater than the pair p4.  
```  
  
##  <a name="op_gt_eq"></a>  Operátor&gt;=  
 Testy, pokud objekt dvojice na levé straně operátoru je větší než nebo rovno objekt dvojice na pravé straně.  
  
```  
template <class Type>  
constexpr bool operator>=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator>=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `pair` na levé straně operátoru.  
  
 `right`  
 Objekt typu `pair` na pravé straně operátoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `pair` na levé straně operátoru je větší než nebo rovno `pair` na pravé straně operátoru; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání páry první prvky dvě dvojice hodnot se mají vyšší prioritu. Pokud se liší, je výsledkem porovnávání považován za výsledku porovnání, které odpovídá páru. Pokud nejsou různé hodnoty první elementů, porovnání hodnot druhý elementů a výsledek jejich porovnání se používá jako výsledek porovnání, které odpovídá páru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// utility_op_ge.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 >= p2 )  
      cout << "Pair p1 is greater than or equal to pair p2." << endl;  
   else  
      cout << "The pair p1 is less than the pair p2." << endl;  
  
   if ( p1 >= p3 )  
      cout << "Pair p1 is greater than or equal to pair p3." << endl;  
   else  
      cout << "The pair p1 is less than the pair p3." << endl;  
  
   if ( p1 >= p4 )  
      cout << "Pair p1 is greater than or equal to pair p4." << endl;  
   else  
      cout << "The pair p1 is less than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is less than the pair p2.  
Pair p1 is greater than or equal to pair p3.  
Pair p1 is greater than or equal to pair p4.  
```  
  
## <a name="see-also"></a>Viz také  
 [\<nástroj >](../standard-library/utility.md)

