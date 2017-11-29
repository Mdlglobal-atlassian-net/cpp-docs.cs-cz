---
title: "&lt;Mapa&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- map/std::operator!=
- map/std::operator&gt;
- map/std::operator&gt;=
- map/std::operator&lt;
- map/std::operator&lt;=
- map/std::operator==
dev_langs: C++
ms.assetid: 7df02b9f-701c-44ed-834a-a819badc5bd0
caps.latest.revision: "7"
manager: ghogen
helpviewer_keywords:
- std::operator!= (map)
- std::operator&gt; (map)
- std::operator&gt;= (map)
- std::operator&lt; (map)
- std::operator&lt;= (map)
- std::operator== (map)
ms.openlocfilehash: 6b2eb6b5ab3a8b08af5375b7767328289c68a744
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltmapgt-operators"></a>&lt;Mapa&gt; operátory
||||  
|-|-|-|  
|[Operator! =](#op_neq)|[operátor&gt;](#op_gt)|[operátor&gt;=](#op_gt_eq)|  
|[operátor&lt;](#op_lt)|[operátor&lt;=](#op_lt_eq)|[Operator ==](#op_eq_eq)|  
|[Operator! = (multimap)](#op_neq_multimap)|[operátor&gt;](#op_gt_multimap)|[operátor&gt;=](#op_gt_eq_multimap)|  
|[operátor&lt;](#op_lt_multimap)|[operátor&lt;=](#op_lt_eq_multimap)|[Operator ==](#op_eq_eq_multimap)|  
  
##  <a name="op_neq"></a>Operator! =  
 Testy, pokud objekt mapy na levé straně operátoru není stejný jako mapy objekt na pravé straně.  
  
```
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **mapy**.  
  
 `right`  
 Objekt typu **mapy**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud map není stejný; **false** Pokud mapy jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi map – objekty je založena na pairwise porovnání jejich součástí. Dvě mapy jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// map_op_ne.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1, m2, m3;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 != m2 )  
      cout << "The maps m1 and m2 are not equal." << endl;  
   else  
      cout << "The maps m1 and m2 are equal." << endl;  
  
   if ( m1 != m3 )  
      cout << "The maps m1 and m3 are not equal." << endl;  
   else  
      cout << "The maps m1 and m3 are equal." << endl;  
}  
\* Output:   
The maps m1 and m2 are not equal.  
The maps m1 and m3 are equal.  
*\  
```  
  
##  <a name="op_lt"></a>operátor&lt;  
 Testy, pokud je objekt mapy na levé straně operátoru menší než mapy objekt na pravé straně.  
  
```
bool operator<(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **mapy**.  
  
 `right`  
 Objekt typu **mapy**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud mapa na levé straně operátoru je striktně menší než mapy na pravé straně operátoru; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi map – objekty je založena na pairwise porovnání jejich součástí. Je menší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// map_op_lt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map<int, int> m1, m2, m3;  
   int i;  
   typedef pair<int, int> Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 < m2 )  
      cout << "The map m1 is less than the map m2." << endl;  
   else  
      cout << "The map m1 is not less than the map m2." << endl;  
  
   if ( m1 < m3 )  
      cout << "The map m1 is less than the map m3." << endl;  
   else  
      cout << "The map m1 is not less than the map m3." << endl;  
}  
\* Output:   
The map m1 is less than the map m2.  
The map m1 is not less than the map m3.  
*\  
```  
  
##  <a name="op_lt_eq"></a>operátor&lt;=  
 Pokud mapy objekt na levé straně operátoru testů je menší než nebo rovno mapy objekt na pravé straně.  
  
```
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **mapy**.  
  
 `right`  
 Objekt typu **mapy**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud mapy na levé straně operátoru je menší než nebo rovná mapy na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// map_op_le.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1, m2, m3, m4;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 <= m2 )  
      cout << "The map m1 is less than or equal to the map m2." << endl;  
   else  
      cout << "The map m1 is greater than the map m2." << endl;  
  
   if ( m1 <= m3 )  
      cout << "The map m1 is less than or equal to the map m3." << endl;  
   else  
      cout << "The map m1 is greater than the map m3." << endl;  
  
   if ( m1 <= m4 )  
      cout << "The map m1 is less than or equal to the map m4." << endl;  
   else  
      cout << "The map m1 is greater than the map m4." << endl;  
}  
\* Output:   
The map m1 is less than or equal to the map m2.  
The map m1 is greater than the map m3.  
The map m1 is less than or equal to the map m4.  
*\  
```  
  
##  <a name="op_eq_eq"></a>Operator ==  
 Testy, pokud objekt mapy na levé straně operátoru rovná mapy objekt na pravé straně.  
  
```
bool operator==(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **mapy**.  
  
 `right`  
 Objekt typu **mapy**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud mapy na levé straně operátoru rovná mapy na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi map – objekty je založena na pairwise porovnání jejich součástí. Dvě mapy jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// map_op_eq.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 == m2 )  
      cout << "The maps m1 and m2 are equal." << endl;  
   else  
      cout << "The maps m1 and m2 are not equal." << endl;  
  
   if ( m1 == m3 )  
      cout << "The maps m1 and m3 are equal." << endl;  
   else  
      cout << "The maps m1 and m3 are not equal." << endl;  
}  
\* Output:   
The maps m1 and m2 are not equal.  
The maps m1 and m3 are equal.  
*\  
```  
  
##  <a name="op_gt"></a>operátor&gt;  
 Testy, pokud objekt mapy na levé straně operátoru je větší než mapy objekt na pravé straně.  
  
```
bool operator>(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **mapy**.  
  
 `right`  
 Objekt typu **mapy**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud mapy na levé straně operátoru je větší než mapy na pravé straně operátoru jinak **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi map – objekty je založena na pairwise porovnání jejich součástí. Delší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// map_op_gt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 > m2 )  
      cout << "The map m1 is greater than the map m2." << endl;  
   else  
      cout << "The map m1 is not greater than the map m2." << endl;  
  
   if ( m1 > m3 )  
      cout << "The map m1 is greater than the map m3." << endl;  
   else  
      cout << "The map m1 is not greater than the map m3." << endl;  
}  
\* Output:   
The map m1 is not greater than the map m2.  
The map m1 is greater than the map m3.  
*\  
```  
  
##  <a name="op_gt_eq"></a>operátor&gt;=  
 Testy, pokud se mapování objekt na levé straně operátoru větší než nebo rovna hodnotě mapy objekt na pravé straně.  
  
```
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **mapy**.  
  
 `right`  
 Objekt typu **mapy**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud mapa na levé straně operátoru je větší než nebo rovná mapy na pravé straně seznamu; jinak hodnota **false**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// map_op_ge.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map < int, int > m1, m2, m3, m4;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 >= m2 )  
      cout << "Map m1 is greater than or equal to map m2." << endl;  
   else  
      cout << "The map m1 is less than the map m2." << endl;  
  
   if ( m1 >= m3 )  
      cout << "Map m1 is greater than or equal to map m3." << endl;  
   else  
      cout << "The map m1 is less than the map m3." << endl;  
  
   if ( m1 >= m4 )  
      cout << "Map m1 is greater than or equal to map m4." << endl;  
   else  
      cout << "The map m1 is less than the map m4." << endl;  
}  
\* Output:   
The map m1 is less than the map m2.  
Map m1 is greater than or equal to map m3.  
Map m1 is greater than or equal to map m4.  
*\  
```  
  
##  <a name="op_neq_multimap"></a>Operator! = (multimap)  
 Testy, pokud multimap objekt na levé straně operátoru není stejný jako multimap objekt na pravé straně.  
  
```
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multimap`.  
  
 `right`  
 Objekt typu `multimap`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multimaps není stejný; **false** Pokud multimaps jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi multimap objekty je založena na pairwise porovnání jejich součástí. Dva multimaps jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multimap_op_ne.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1, m2, m3;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 != m2 )  
      cout << "The multimaps m1 and m2 are not equal." << endl;  
   else  
      cout << "The multimaps m1 and m2 are equal." << endl;  
  
   if ( m1 != m3 )  
      cout << "The multimaps m1 and m3 are not equal." << endl;  
   else  
      cout << "The multimaps m1 and m3 are equal." << endl;  
}  
\* Output:   
The multimaps m1 and m2 are not equal.  
The multimaps m1 and m3 are equal.  
*\  
```  
  
##  <a name="op_lt_multimap"></a>operátor&lt;  
 Testy, pokud multimap objekt na levé straně operátor je menší než multimap objekt na pravé straně.  
  
```
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multimap`.  
  
 `right`  
 Objekt typu `multimap`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multimap na levé straně operátoru je striktně menší než multimap na pravé straně operátoru; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi multimap objekty je založena na pairwise porovnání jejich součástí. Je menší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multimap_op_lt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 < m2 )  
      cout << "The multimap m1 is less than the multimap m2." << endl;  
   else  
      cout << "The multimap m1 is not less than the multimap m2." << endl;  
  
   if ( m1 < m3 )  
      cout << "The multimap m1 is less than the multimap m3." << endl;  
   else  
      cout << "The multimap m1 is not less than the multimap m3." << endl;  
}  
\* Output:   
The multimap m1 is less than the multimap m2.  
The multimap m1 is not less than the multimap m3.  
*\  
```  
  
##  <a name="eq_multimap"></a>operátor&lt;=  
 Pokud multimap objekt na levé straně operátoru testů je menší než nebo rovna hodnotě multimap objekt na pravé straně.  
  
```
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multimap`.  
  
 `right`  
 Objekt typu `multimap`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multimap na levé straně operátoru je menší než nebo rovná multimap na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multimap_op_le.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1, m2, m3, m4;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 <= m2 )  
      cout << "m1 is less than or equal to m2" << endl;  
   else  
      cout << "m1 is greater than m2" << endl;  
  
   if ( m1 <= m3 )  
      cout << "m1 is less than or equal to m3" << endl;  
   else  
      cout << "m1 is greater than m3" << endl;  
  
   if ( m1 <= m4 )  
      cout << "m1 is less than or equal to m4" << endl;  
   else  
      cout << "m1 is greater than m4" << endl;  
}  
\* Output:   
m1 is less than or equal to m2  
m1 is greater than m3  
m1 is less than or equal to m4  
*\  
```  
  
##  <a name="op_eq_eq_multimap"></a>Operator ==  
 Testy, pokud multimap objekt na levé straně operátoru rovná multimap objekt na pravé straně.  
  
```
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multimap`.  
  
 `right`  
 Objekt typu `multimap`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multimap na levé straně operátoru rovná multimap na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi multimap objekty je založena na pairwise porovnání jejich součástí. Dva multimaps jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multimap_op_eq.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap<int, int> m1, m2, m3;  
   int i;  
   typedef pair<int, int> Int_Pair;  
  
   for (i = 0; i < 3; i++)  
   {  
      m1.insert(Int_Pair(i, i));  
      m2.insert(Int_Pair(i, i*i));  
      m3.insert(Int_Pair(i, i));  
   }  
  
   if ( m1 == m2 )  
      cout << "m1 and m2 are equal" << endl;  
   else  
      cout << "m1 and m2 are not equal" << endl;  
  
   if ( m1 == m3 )  
      cout << "m1 and m3 are equal" << endl;  
   else  
      cout << "m1 and m3 are not equal" << endl;  
}  
\* Output:   
m1 and m2 are not equal  
m1 and m3 are equal  
*\  
```  
  
##  <a name="op_gt_multimap"></a>operátor&gt;  
 Testy, pokud multimap objekt na levé straně operátoru je větší než multimap objekt na pravé straně.  
  
```
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multimap`.  
  
 `right`  
 Objekt typu `multimap`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multimap na levé straně operátoru je větší než multimap na pravé straně operátoru jinak **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi multimap objekty je založena na pairwise porovnání jejich součástí. Delší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multimap_op_gt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 > m2 )  
      cout << "The multimap m1 is greater than the multimap m2." << endl;  
   else  
      cout << "Multimap m1 is not greater than multimap m2." << endl;  
  
   if ( m1 > m3 )  
      cout << "The multimap m1 is greater than the multimap m3." << endl;  
   else  
      cout << "The multimap m1 is not greater than the multimap m3." << endl;  
}  
\* Output:   
Multimap m1 is not greater than multimap m2.  
The multimap m1 is greater than the multimap m3.  
*\  
```  
  
##  <a name="op_gt_eq_multimap"></a>operátor&gt;=  
 Testy, pokud se multimap objekt na levé straně operátoru větší než nebo rovna hodnotě multimap objekt na pravé straně.  
  
```
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multimap`.  
  
 `right`  
 Objekt typu `multimap`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multimap na levé straně operátoru je větší než nebo rovná multimap na pravé straně seznamu; jinak hodnota **false**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multimap_op_ge.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap < int, int > m1, m2, m3, m4;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 >= m2 )  
      cout << "The multimap m1 is greater than or equal to the multimap m2." << endl;  
   else  
      cout << "The multimap m1 is less than the multimap m2." << endl;  
  
   if ( m1 >= m3 )  
      cout << "The multimap m1 is greater than or equal to the multimap m3." << endl;  
   else  
      cout << "The multimap m1 is less than the multimap m3." << endl;  
  
   if ( m1 >= m4 )  
      cout << "The multimap m1 is greater than or equal to the multimap m4." << endl;  
   else  
      cout << "The multimap m1 is less than the multimap m4." << endl;  
}  
\* Output:   
The multimap m1 is less than the multimap m2.  
The multimap m1 is greater than or equal to the multimap m3.  
The multimap m1 is greater than or equal to the multimap m4.  
*\  
```  
  
## <a name="see-also"></a>Viz také  
 [\<Mapa >](../standard-library/map.md)


