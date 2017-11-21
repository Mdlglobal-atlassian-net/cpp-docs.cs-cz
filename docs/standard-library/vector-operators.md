---
title: "&lt;vektor&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vector/std::operator!=
- vector/std::operator&gt;
- vector/std::operator&gt;=
- vector/std::operator&lt;
- vector/std::operator&lt;=
- vector/std::operator==
dev_langs: C++
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
caps.latest.revision: "13"
manager: ghogen
helpviewer_keywords:
- std::operator!= (vector)
- std::operator&gt; (vector)
- std::operator&gt;= (vector)
- std::operator&lt; (vector)
- std::operator&lt;= (vector)
- std::operator== (vector)
ms.openlocfilehash: 310bf81e6dd20440c57ce5a0c73da7a6919f0015
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltvectorgt-operators"></a>&lt;vektor&gt; operátory
||||  
|-|-|-|  
|[Operator! =](#op_neq)|[operátor&gt;](#op_gt)|[operátor&gt;=](#op_gt_eq)|  
|[operátor&lt;](#op_lt)|[operátor&lt;=](#op_lt_eq)|[Operator ==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>Operator! =  
 Testy, pokud objekt na levé straně operátoru není stejný jako objekt na pravé straně.  
  
```  
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **vektoru**.  
  
 `right`  
 Objekt typu **vektoru**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud vektory není stejný; **false** Pokud vektory jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Dva vektory jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// vector_op_ne.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
     v2.push_back( 2 );  
  
   if ( v1 != v2 )  
      cout << "Vectors not equal." << endl;  
   else  
      cout << "Vectors equal." << endl;  
}  
```  
  
```Output  
Vectors not equal.  
```  
  
##  <a name="op_lt"></a>operátor&lt;  
 Testy, pokud je objekt na levé straně operátoru menší než objekt na pravé straně.  
  
```  
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **vektoru**.  
  
 `right`  
 Objekt typu **vektoru**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud vektoru na levé straně operátoru je menší než vektoru na pravé straně operátoru; v opačném případě **false**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// vector_op_lt.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 4 );  
  
   v2.push_back( 1 );  
   v2.push_back( 3 );  
  
   if ( v1 < v2 )  
      cout << "Vector v1 is less than vector v2." << endl;  
   else  
      cout << "Vector v1 is not less than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is less than vector v2.  
```  
  
##  <a name="op_lt_eq"></a>operátor&lt;=  
 Testy, pokud je objekt na levé straně operátoru menší než nebo rovna hodnotě objekt na pravé straně.  
  
```  
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **vektoru**.  
  
 `right`  
 Objekt typu **vektoru**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud vektoru na levé straně operátoru je menší než nebo rovná vektoru na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// vector_op_le.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 4 );  
  
   v2.push_back( 1 );  
   v2.push_back( 3 );  
  
   if ( v1 <= v2 )  
      cout << "Vector v1 is less than or equal to vector v2." << endl;  
   else  
      cout << "Vector v1 is greater than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is less than or equal to vector v2.  
```  
  
##  <a name="op_eq_eq"></a>Operator ==  
 Testy, pokud je objekt na levé straně operátoru stejný objekt na pravé straně.  
  
```  
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **vektoru**.  
  
 `right`  
 Objekt typu **vektoru**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud vektoru na levé straně operátoru rovná vektoru na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Dva vektory jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// vector_op_eq.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v2.push_back( 1 );  
  
   if ( v1 == v2 )  
      cout << "Vectors equal." << endl;  
   else  
      cout << "Vectors not equal." << endl;  
}  
```  
  
```Output  
Vectors equal.  
```  
  
##  <a name="op_gt"></a>operátor&gt;  
 Testy, pokud je objekt na levé straně operátoru větší než objekt na pravé straně.  
  
```  
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **vektoru**.  
  
 `right`  
 Objekt typu **vektoru**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud vektoru na levé straně operátoru je větší než vektoru na pravé straně operátoru jinak **false**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// vector_op_gt.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 3 );  
   v1.push_back( 1 );  
  
   v2.push_back( 1 );  
   v2.push_back( 2 );  
   v2.push_back( 2 );  
  
   if ( v1 > v2 )  
      cout << "Vector v1 is greater than vector v2." << endl;  
   else  
      cout << "Vector v1 is not greater than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is greater than vector v2.  
```  
  
##  <a name="op_gt_eq"></a>operátor&gt;=  
 Testy, pokud je objekt na levé straně operátoru větší než nebo rovna hodnotě objekt na pravé straně.  
  
```  
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **vektoru**.  
  
 `right`  
 Objekt typu **vektoru**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud vektoru na levé straně operátoru je větší než nebo rovná vektoru na pravé straně vektoru; jinak hodnota **false**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// vector_op_ge.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 3 );  
   v1.push_back( 1 );  
  
     v2.push_back( 1 );  
   v2.push_back( 2 );  
   v2.push_back( 2 );  
  
   if ( v1 >= v2 )  
      cout << "Vector v1 is greater than or equal to vector v2." << endl;  
   else  
      cout << "Vector v1 is less than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is greater than or equal to vector v2.  
```  
  
## <a name="see-also"></a>Viz také  
 [\<vektor >](../standard-library/vector.md)

