---
title: "&lt;hash_set –&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
dev_langs: C++
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
caps.latest.revision: "13"
manager: ghogen
ms.openlocfilehash: e5205240d4f0bbfbf41423ee73a737e7d2bd0667
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="lthashsetgt-operators"></a>&lt;hash_set –&gt; operátory
||||  
|-|-|-|  
|[Operator! =](#op_neq)|[Operator! = (hash_multiset)](#op_neq_hash_multiset)|[Operator ==](#op_eq_eq)|  
|[Operator == (hash_multiset)](#op_eq_eq_hash_multiset)|  
  
##  <a name="op_neq"></a>Operator! =  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).  
  
 Testy, pokud hash_set objekt na levé straně operátoru není stejný jako hash_set objekt na pravé straně.  
  
```  
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `hash_set`.  
  
 `right`  
 Objekt typu `hash_set`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud hash_sets není stejný; **false** Pokud hash_sets jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi hash_set – objekty je založena na pairwise porovnání mezi jejich elementů. Dva hash_sets jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
 Členové [< hash_map >](../standard-library/hash-map.md) a [< hash_set >](../standard-library/hash-set.md) hlavičkových souborů jsou v [stdext – Namespace](../standard-library/stdext-namespace.md).
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_set_op_ne.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1, hs2, hs3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      hs1.insert ( i );  
      hs2.insert ( i * i );  
      hs3.insert ( i );  
   }  
  
   if ( hs1 != hs2 )  
      cout << "The hash_sets hs1 and hs2 are not equal." << endl;  
   else  
      cout << "The hash_sets hs1 and hs2 are equal." << endl;  
  
   if ( hs1 != hs3 )  
      cout << "The hash_sets hs1 and hs3 are not equal." << endl;  
   else  
      cout << "The hash_sets hs1 and hs3 are equal." << endl;  
}  
```  
  
```Output  
The hash_sets hs1 and hs2 are not equal.  
The hash_sets hs1 and hs3 are equal.  
```  
  
##  <a name="op_eq_eq"></a>Operator ==  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).  
  
 Testy, pokud hash_set objekt na levé straně operátoru rovná hash_set objekt na pravé straně.  
  
```  
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `hash_set`.  
  
 `right`  
 Objekt typu `hash_set`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud hash_set na levé straně operátoru rovná hash_set na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi hash_set – objekty je založena na pairwise porovnání jejich součástí. Dva hash_sets jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_set_op_eq.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 == s2 )  
      cout << "The hash_sets s1 and s2 are equal." << endl;  
   else  
      cout << "The hash_sets s1 and s2 are not equal." << endl;  
  
   if ( s1 == s3 )  
      cout << "The hash_sets s1 and s3 are equal." << endl;  
   else  
      cout << "The hash_sets s1 and s3 are not equal." << endl;  
}  
```  
  
```Output  
The hash_sets s1 and s2 are not equal.  
The hash_sets s1 and s3 are equal.  
```  
  
##  <a name="neq_hash_multiset"></a>Operator! = (hash_multiset)  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).  
  
 Testy, pokud hash_multiset objekt na levé straně operátoru není stejný jako hash_multiset objekt na pravé straně.  
  
```  
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `hash_multiset`.  
  
 `right`  
 Objekt typu `hash_multiset`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud hash_multisets není stejný; **false** Pokud hash_multisets jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi hash_multiset – objekty je založena na pairwise porovnání mezi jejich elementů. Dva hash_multisets jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
   
  
### <a name="example"></a>Příklad  
  
```cpp  
// hashset_op_ne.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hs1, hs2, hs3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      hs1.insert ( i );  
      hs2.insert ( i * i );  
      hs3.insert ( i );  
   }  
  
   if ( hs1 != hs2 )  
      cout << "The hash_multisets hs1 and hs2 are not equal." << endl;  
   else  
      cout << "The hash_multisets hs1 and hs2 are equal." << endl;  
  
   if ( hs1 != hs3 )  
      cout << "The hash_multisets hs1 and hs3 are not equal." << endl;  
   else  
      cout << "The hash_multisets hs1 and hs3 are equal." << endl;  
}  
```  
  
```Output  
The hash_multisets hs1 and hs2 are not equal.  
The hash_multisets hs1 and hs3 are equal.  
```  
  
##  <a name="eq_eq_hash_multiset"></a>Operator == (hash_multiset)  
  
> [!NOTE]
>  Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).  
  
 Testy, pokud hash_multiset objekt na levé straně operátoru rovná hash_multiset objekt na pravé straně.  
  
```  
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `hash_multiset`.  
  
 `right`  
 Objekt typu `hash_multiset`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud hash_multiset na levé straně operátoru rovná hash_multiset na pravé straně operátoru; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi hash_multiset – objekty je založena na pairwise porovnání jejich součástí. Dva hash_multisets jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// hash_multiset_op_eq.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 == s2 )  
      cout << "The hash_multisets s1 and s2 are equal." << endl;  
   else  
      cout << "The hash_multisets s1 and s2 are not equal." << endl;  
  
   if ( s1 == s3 )  
      cout << "The hash_multisets s1 and s2 are equal." << endl;  
   else  
      cout << "The hash_multisets s1 and s2 are not equal." << endl;  
}  
```  
  
```Output  
The hash_multisets s1 and s2 are not equal.  
The hash_multisets s1 and s2 are equal.  
```  
  
## <a name="see-also"></a>Viz také  
 [< hash_set >](../standard-library/hash-set.md)
