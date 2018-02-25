---
title: "&lt;nastavit&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- set/std::operator!=
- set/std::operator&gt;
- set/std::operator&gt;=
- set/std::operator&lt;
- set/std::operator&lt;=
- set/std::operator==
dev_langs:
- C++
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::operator!= (set)
- std::operator&gt; (set)
- std::operator&gt;= (set)
- std::operator&lt; (set)
- std::operator&lt;= (set)
- std::operator== (set)
ms.openlocfilehash: d5058b75af8b26b6e7ddc9a8a7b487b0cd8b8e91
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltsetgt-operators"></a>&lt;nastavit&gt; operátory
||||  
|-|-|-|  
|[Operator! = (set)](#op_neq)|[operátor&gt; (set)](#op_gt)|[operátor&gt;= (set)](#eq)|  
|[operátor&lt; (set)](#op_lt)|[operátor&lt;= (set)](#eq)|[operator== (set)](#op_eq_eq)|  
|[operator!= (multiset)](#op_neq_multiset)|[operator&gt; (multiset)](#op_gt_multiset)|[operator&gt;= (multiset)](#op_gt_eq_multiset)|  
|[operator&lt; (multiset)](#op_lt_multiset)|[operator&lt;= (multiset)](#op_lt_eq_multiset)|[operator== (multiset)](#op_eq_eq_multiset)|  
  
##  <a name="op_neq">Operator! = (set)</a>  
 Testy, pokud sada objekt na levé straně operátoru není stejný jako sada objekt na pravé straně.  
  
```
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **nastavit**.  
  
 `right`  
 Objekt typu **nastavit**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud sady není stejný; **false** Pokud sady jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi objekty sada je založená na pairwise porovnání mezi jejich elementů. Dvě sady jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// set_op_ne.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 != s2 )  
      cout << "The sets s1 and s2 are not equal." << endl;  
   else  
      cout << "The sets s1 and s2 are equal." << endl;  
  
   if ( s1 != s3 )  
      cout << "The sets s1 and s3 are not equal." << endl;  
   else  
      cout << "The sets s1 and s3 are equal." << endl;  
}  
\* Output:   
The sets s1 and s2 are not equal.  
The sets s1 and s3 are equal.  
*\  
```  
  
##  <a name="op_lt"></a>  operátor&lt; (set)  
 Testy, pokud je sada objekt na levé straně operátoru menší než sadu objekt na pravé straně.  
  
```
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **nastavit**.  
  
 `right`  
 Objekt typu **nastavit**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud sada na levé straně operátoru je striktně menší než sadu na pravé straně operátoru; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi objekty sad je založena na pairwise porovnání jejich součástí. Je menší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// set_op_lt.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
   }  
  
   if ( s1 < s2 )  
      cout << "The set s1 is less than the set s2." << endl;  
   else  
      cout << "The set s1 is not less than the set s2." << endl;  
  
   if ( s1 < s3 )  
      cout << "The set s1 is less than the set s3." << endl;  
   else  
      cout << "The set s1 is not less than the set s3." << endl;  
}  
\* Output:   
The set s1 is less than the set s2.  
The set s1 is not less than the set s3.  
*\  
```  
  
##  <a name="op_lt_eq"></a>  operátor&lt;= (set)  
 Testy, pokud sada objekt na levé straně operátoru je menší než nebo stejný jako sada objekt na pravé straně.  
  
```
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **nastavit**.  
  
 `right`  
 Objekt typu **nastavit**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud sada na levé straně operátoru je menší než nebo rovná sadu na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi objekty sad je založena na pairwise porovnání jejich součástí. Je menší než nebo rovna na relaci mezi dvěma objekty je založena na porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// set_op_le.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3, s4;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
      s4.insert ( i );  
   }  
  
   if ( s1 <= s2 )  
      cout << "Set s1 is less than or equal to the set s2." << endl;  
   else  
      cout << "The set s1 is greater than the set s2." << endl;  
  
   if ( s1 <= s3 )  
      cout << "Set s1 is less than or equal to the set s3." << endl;  
   else  
      cout << "The set s1 is greater than the set s3." << endl;  
  
   if ( s1 <= s4 )  
      cout << "Set s1 is less than or equal to the set s4." << endl;  
   else  
      cout << "The set s1 is greater than the set s4." << endl;  
}  
\* Output:   
Set s1 is less than or equal to the set s2.  
The set s1 is greater than the set s3.  
Set s1 is less than or equal to the set s4.  
*\  
```  
  
##  <a name="op_eq_eq"></a>  Operator == (set)  
 Testy, pokud sada objekt na levé straně operátoru rovná sadu objekt na pravé straně.  
  
```
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **nastavit**.  
  
 `right`  
 Objekt typu **nastavit**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je sada na levé straně operátoru rovná sadu na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi objekty sad je založena na pairwise porovnání jejich součástí. Dvě sady jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// set_op_eq.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 == s2 )  
      cout << "The sets s1 and s2 are equal." << endl;  
   else  
      cout << "The sets s1 and s2 are not equal." << endl;  
  
   if ( s1 == s3 )  
      cout << "The sets s1 and s3 are equal." << endl;  
   else  
      cout << "The sets s1 and s3 are not equal." << endl;  
}  
\* Output:   
The sets s1 and s2 are not equal.  
The sets s1 and s3 are equal.  
*\  
```  
  
##  <a name="op_gt"></a>  operátor&gt; (set)  
 Testy, pokud je sada objekt na levé straně operátoru větší než sadu objekt na pravé straně.  
  
```
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **nastavit**.  
  
 `right`  
 Objekt typu **nastavit**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud sada na levé straně operátoru je větší než sadu na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi objekty sad je založena na pairwise porovnání jejich součástí. Delší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// set_op_gt.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
   }  
  
   if ( s1 > s2 )  
      cout << "The set s1 is greater than the set s2." << endl;  
   else  
      cout << "The set s1 is not greater than the set s2." << endl;  
  
   if ( s1 > s3 )  
      cout << "The set s1 is greater than the set s3." << endl;  
   else  
      cout << "The set s1 is not greater than the set s3." << endl;  
}  
\* Output:   
The set s1 is not greater than the set s2.  
The set s1 is greater than the set s3.  
*\  
```  
  
##  <a name="op_gt_eq"></a>  operátor&gt;= (set)  
 Testy, pokud je sada objekt na levé straně operátoru větší než nebo rovna hodnotě sadu objekt na pravé straně.  
  
```
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu **nastavit**.  
  
 `right`  
 Objekt typu **nastavit**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud sada na levé straně operátoru je větší než nebo rovná sadu na pravé straně seznamu; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi objekty sad je založena na pairwise porovnání jejich součástí. Větší než nebo rovna hodnotě vztah mezi dvěma objekty podle porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// set_op_ge.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3, s4;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
      s4.insert ( i );  
   }  
  
   if ( s1 >= s2 )  
      cout << "Set s1 is greater than or equal to set s2." << endl;  
   else  
      cout << "The set s1 is less than the set s2." << endl;  
  
   if ( s1 >= s3 )  
      cout << "Set s1 is greater than or equal to set s3." << endl;  
   else  
      cout << "The set s1 is less than the set s3." << endl;  
  
   if ( s1 >= s4 )  
      cout << "Set s1 is greater than or equal to set s4." << endl;  
   else  
      cout << "The set s1 is less than the set s4." << endl;  
}  
\* Output:   
The set s1 is less than the set s2.  
Set s1 is greater than or equal to set s3.  
Set s1 is greater than or equal to set s4.  
*\  
```  
  
##  <a name="op_neq_multiset"></a>  Operator! = (multiset)  
 Testy, pokud multiset objekt na levé straně operátoru není stejný jako multiset objekt na pravé straně.  
  
```
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multiset`.  
  
 `right`  
 Objekt typu `multiset`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multisets nebo sady nejsou stejné; **false** Pokud multisets nebo sady jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi multiset – objekty je založena na pairwise porovnání mezi jejich elementů. Dvě sady nebo multisets jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multiset_op_ne.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 != s2 )  
      cout << "The multisets s1 and s2 are not equal." << endl;  
   else  
      cout << "The multisets s1 and s2 are equal." << endl;  
  
   if ( s1 != s3 )  
      cout << "The multisets s1 and s3 are not equal." << endl;  
   else  
      cout << "The multisets s1 and s3 are equal." << endl;  
}  
\* Output:   
The multisets s1 and s2 are not equal.  
The multisets s1 and s3 are equal.  
*\  
```  
  
##  <a name="op_lt_multiset"></a>  operátor&lt; (multiset)  
 Testy, pokud multiset objekt na levé straně operátor je menší než multiset objekt na pravé straně.  
  
```
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multiset`.  
  
 `right`  
 Objekt typu `multiset`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multimnožina na levé straně operátoru je striktně menší než multiset na pravé straně operátoru; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi multiset – objekty je založena na pairwise porovnání jejich součástí. Je menší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multiset_op_lt.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
   }  
  
   if ( s1 < s2 )  
      cout << "The multiset s1 is less than "  
           << "the multiset s2." << endl;  
   else  
      cout << "The multiset s1 is not less than "  
           << "the multiset s2." << endl;  
  
   if ( s1 < s3 )  
      cout << "The multiset s1 is less than "  
           << "the multiset s3." << endl;  
   else  
      cout << "The multiset s1 is not less than "  
           << "the multiset s3." << endl;  
}  
\* Output:   
The multiset s1 is less than the multiset s2.  
The multiset s1 is not less than the multiset s3.  
*\  
```  
  
##  <a name="op_lt_eq_multiset"></a>  operátor&lt;= (multiset)  
 Pokud multiset objekt na levé straně operátoru testů je menší než nebo rovna hodnotě multiset objekt na pravé straně.  
  
```
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multiset`.  
  
 `right`  
 Objekt typu `multiset`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multimnožina na levé straně operátoru je menší než nebo rovná multiset na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi multiset – objekty je založena na pairwise porovnání jejich součástí. Je menší než nebo rovna na relaci mezi dvěma objekty je založena na porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multiset_op_le.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3, s4;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
      s4.insert ( i );  
   }  
  
   if ( s1 <= s2 )  
      cout << "The multiset s1 is less than "  
           << "or equal to the multiset s2." << endl;  
   else  
      cout << "The multiset s1 is greater than "  
           << "the multiset s2." << endl;  
  
   if ( s1 <= s3 )  
      cout << "The multiset s1 is less than "  
           << "or equal to the multiset s3." << endl;  
   else  
      cout << "The multiset s1 is greater than "  
           << "the multiset s3." << endl;  
  
   if ( s1 <= s4 )  
      cout << "The multiset s1 is less than "  
           << "or equal to the multiset s4." << endl;  
   else  
      cout << "The multiset s1 is greater than "  
           << "the multiset s4." << endl;  
}  
\* Output:   
The multiset s1 is less than or equal to the multiset s2.  
The multiset s1 is greater than the multiset s3.  
The multiset s1 is less than or equal to the multiset s4.  
*\  
```  
  
##  <a name="op_eq_eq_multiset"></a>  Operator == (multiset)  
 Testy, pokud multiset objekt na levé straně operátoru rovná multiset objekt na pravé straně.  
  
```
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multiset`.  
  
 `right`  
 Objekt typu `multiset`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multimnožina na levé straně operátor je rovno multiset na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi multiset – objekty je založena na pairwise porovnání jejich součástí. Dvě sady nebo multisets jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multiset_op_eq.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 == s2 )  
      cout << "The multisets s1 and s2 are equal." << endl;  
   else  
      cout << "The multisets s1 and s2 are not equal." << endl;  
  
   if ( s1 == s3 )  
      cout << "The multisets s1 and s3 are equal." << endl;  
   else  
      cout << "The multisets s1 and s3 are not equal." << endl;  
}  
\* Output:   
The multisets s1 and s2 are not equal.  
The multisets s1 and s3 are equal.  
*\  
```  
  
##  <a name="op_gt_multiset"></a>  operátor&gt; (multiset)  
 Testy, pokud multiset objekt na levé straně operátoru je větší než multiset objekt na pravé straně.  
  
```
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multiset`.  
  
 `right`  
 Objekt typu `multiset`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multimnožina na levé straně operátoru je větší než multiset na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi multiset – objekty je založena na pairwise porovnání jejich součástí. Delší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multiset_op_gt.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
   }  
  
   if ( s1 > s2 )  
      cout << "The multiset s1 is greater than "  
           << "the multiset s2." << endl;  
   else  
      cout << "The multiset s1 is not greater "  
           << "than the multiset s2." << endl;  
  
   if ( s1 > s3 )  
      cout << "The multiset s1 is greater than "  
           << "the multiset s3." << endl;  
   else  
      cout << "The multiset s1 is not greater than "  
           << "the multiset s3." << endl;  
}  
\* Output:   
The multiset s1 is not greater than the multiset s2.  
The multiset s1 is greater than the multiset s3.  
*\  
```  
  
##  <a name="op_gt_eq_multiset"></a>  operátor&gt;= (multiset)  
 Testy, pokud se multiset objekt na levé straně operátoru větší než nebo rovna hodnotě multiset objekt na pravé straně.  
  
```
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `multiset`.  
  
 `right`  
 Objekt typu `multiset`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud multimnožina na levé straně operátoru je větší než nebo rovná multiset na pravé straně seznamu; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi multiset – objekty je založena na pairwise porovnání jejich součástí. Větší než nebo rovna hodnotě vztah mezi dvěma objekty podle porovnání první pár nerovné elementů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// multiset_op_ge.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3, s4;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
      s4.insert ( i );  
   }  
  
   if ( s1 >= s2 )  
      cout << "The multiset s1 is greater than "  
           << "or equal to the multiset s2." << endl;  
   else  
      cout << "The multiset s1 is less than "  
           << "the multiset s2." << endl;  
  
   if ( s1 >= s3 )  
      cout << "The multiset s1 is greater than "  
           << "or equal to the multiset s3." << endl;  
   else  
      cout << "The multiset s1 is less than "  
           << "the multiset s3." << endl;  
  
   if ( s1 >= s4 )  
      cout << "The multiset s1 is greater than "  
           << "or equal to the multiset s4." << endl;  
   else  
      cout << "The multiset s1 is less than "  
           << "the multiset s4." << endl;  
}  
\* Output:   
The multiset s1 is less than the multiset s2.  
The multiset s1 is greater than or equal to the multiset s3.  
The multiset s1 is greater than or equal to the multiset s4.  
*\  
```  
  
## <a name="see-also"></a>Viz také  
 [\<set>](../standard-library/set.md)



