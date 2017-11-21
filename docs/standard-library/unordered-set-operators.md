---
title: "&lt;unordered_set –&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
dev_langs: C++
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
caps.latest.revision: "7"
manager: ghogen
ms.openlocfilehash: 615e2f69a45a17b34b38190ac1c7def1de09d8c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltunorderedsetgt-operators"></a>&lt;unordered_set –&gt; operátory
|||||  
|-|-|-|-|  
|[Operator! =](#op_neq)|[Operator ==](#op_eq_eq)|[Operator! =](#op_neq_unordered_multiset)|[Operator ==](#op_eq_eq_unordered_multiset)|  
  
##  <a name="op_neq"></a>Operator! =  
 Testy jestli [unordered_set](../standard-library/unordered-set-class.md) objekt na levé straně operátoru není stejný jako unordered_set objekt na pravé straně.  
  
```
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `unordered_set`.  
  
 `right`  
 Objekt typu `unordered_set`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud unordered_sets není stejný; `false` Pokud jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi objekty unordered_set nemá vliv libovolný pořadí, ve kterém budou ukládat jejich elementů. Pokud mají stejný počet elementů a prvky v jednom kontejneru jsou Permutace elementů v kontejneru další dva unordered_sets jsou si rovny. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// unordered_set_ne.cpp   
// compile by using: cl.exe /EHsc /nologo /W4 /MTd   
#include <unordered_set>   
#include <iostream>   
#include <ios>  
  
int main()   
{   
    using namespace std;  
  
    unordered_set<char> c1, c2, c3;  
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
    c2.insert('c');   
    c2.insert('a');   
    c2.insert('d');   
  
    c3.insert('c');   
    c3.insert('a');   
    c3.insert('b');   
  
   cout << boolalpha;  
   cout << "c1 != c2: " << (c1 != c2) << endl;   
   cout << "c1 != c3: " << (c1 != c3) << endl;   
   cout << "c2 != c3: " << (c2 != c3) << endl;   
  
    return (0);   
}  
  
```  
  
 **Výstup:**  
  
 `c1 != c2: true`  
  
 `c1 != c3: false`  
  
 `c2 != c3: true`  
  
##  <a name="op_eq_eq"></a>Operator ==  
 Testy jestli [unordered_set](../standard-library/unordered-set-class.md) objekt na levé straně operátoru rovná unordered_set objekt na pravé straně.  
  
```
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `unordered_set`.  
  
 `right`  
 Objekt typu `unordered_set`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud unordered_sets stejný; `false` Pokud nejsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi objekty unordered_set nemá vliv libovolný pořadí, ve kterém budou ukládat jejich elementů. Pokud mají stejný počet elementů a prvky v jednom kontejneru jsou Permutace elementů v kontejneru další dva unordered_sets jsou si rovny. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// unordered_set_eq.cpp   
// compile by using: cl.exe /EHsc /nologo /W4 /MTd   
#include <unordered_set>   
#include <iostream>   
#include <ios>  
  
int main()   
{   
    using namespace std;  
  
    unordered_set<char> c1, c2, c3;  
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
    c2.insert('c');   
    c2.insert('a');   
    c2.insert('d');   
  
    c3.insert('c');   
    c3.insert('a');   
    c3.insert('b');   
  
   cout << boolalpha;  
   cout << "c1 == c2: " << (c1 == c2) << endl;   
   cout << "c1 == c3: " << (c1 == c3) << endl;   
   cout << "c2 == c3: " << (c2 == c3) << endl;   
  
    return (0);   
}  
  
```  
  
 **Výstup:**  
  
 `c1 == c2: false`  
  
 `c1 == c3: true`  
  
 `c2 == c3: false`  
  
##  <a name="op_neq_unordered_multiset"></a>Operator! =  
 Testy jestli [unordered_multiset](../standard-library/unordered-multiset-class.md) objekt na levé straně operátoru není stejný jako unordered_multiset objekt na pravé straně.  
  
```
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `unordered_multiset`.  
  
 `right`  
 Objekt typu `unordered_multiset`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud unordered_multisets není stejný; `false` Pokud jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi objekty unordered_multiset nemá vliv libovolný pořadí, ve kterém budou ukládat jejich elementů. Pokud mají stejný počet elementů a prvky v jednom kontejneru jsou Permutace elementů v kontejneru další dva unordered_multisets jsou si rovny. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// unordered_multiset_ne.cpp   
// compile by using: cl.exe /EHsc /nologo /W4 /MTd   
#include <unordered_set>   
#include <iostream>   
#include <ios>  
  
int main()   
{   
    using namespace std;  
  
    unordered_multiset<char> c1, c2, c3;  
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
    c1.insert('c');   
  
    c2.insert('c');   
    c2.insert('c');   
    c2.insert('a');   
    c2.insert('d');   
  
    c3.insert('c');   
    c3.insert('c');   
    c3.insert('a');   
    c3.insert('b');   
  
   cout << boolalpha;  
   cout << "c1 != c2: " << (c1 != c2) << endl;   
   cout << "c1 != c3: " << (c1 != c3) << endl;   
   cout << "c2 != c3: " << (c2 != c3) << endl;   
  
    return (0);   
}  
  
```  
  
 **Výstup:**  
  
 `c1 != c2: true`  
  
 `c1 != c3: false`  
  
 `c2 != c3: true`  
  
##  <a name="op_eq_eq_unordered_multiset"></a>Operator ==  
 Testy jestli [unordered_multiset](../standard-library/unordered-multiset-class.md) objekt na levé straně operátoru rovná unordered_multiset objekt na pravé straně.  
  
```
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Objekt typu `unordered_multiset`.  
  
 `right`  
 Objekt typu `unordered_multiset`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud unordered_multisets stejný; `false` Pokud nejsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání mezi objekty unordered_multiset nemá vliv libovolný pořadí, ve kterém budou ukládat jejich elementů. Pokud mají stejný počet elementů a prvky v jednom kontejneru jsou Permutace elementů v kontejneru další dva unordered_multisets jsou si rovny. Jinak nerovné.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// unordered_multiset_eq.cpp   
// compile by using: cl.exe /EHsc /nologo /W4 /MTd   
#include <unordered_set>   
#include <iostream>   
#include <ios>  
  
int main()   
{   
    using namespace std;  
  
    unordered_multiset<char> c1, c2, c3;  
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
    c1.insert('c');   
  
    c2.insert('c');   
    c2.insert('c');   
    c2.insert('a');   
    c2.insert('d');   
  
    c3.insert('c');   
    c3.insert('c');   
    c3.insert('a');   
    c3.insert('b');   
  
   cout << boolalpha;  
   cout << "c1 == c2: " << (c1 == c2) << endl;   
   cout << "c1 == c3: " << (c1 == c3) << endl;   
   cout << "c2 == c3: " << (c2 == c3) << endl;   
  
    return (0);   
}  
  
```  
  
 **Výstup:**  
  
 `c1 == c2: false`  
  
 `c1 == c3: true`  
  
 `c2 == c3: false`  
  
## <a name="see-also"></a>Viz také  
 [< unordered_set >](../standard-library/unordered-set.md)



