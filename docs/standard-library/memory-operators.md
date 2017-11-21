---
title: "&lt;paměť&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::operator!=
- memory/std::operator>
- memory/std::operator>=
- memory/std::operator<
- memory/std::operator<=
- memory/std::operator<<
- memory/std::operator==
dev_langs: C++
ms.assetid: 257e3ba9-c4c2-4ae8-9b11-b156ba9c28de
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 95563f5eeb70d33e3ebba4de0aead276a2230669
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltmemorygt-operators"></a>&lt;paměť&gt; operátory
||||  
|-|-|-|  
|[Operator! =](#op_neq)|[operátor&gt;](#op_gt)|[operátor&gt;=](#op_gt_eq)|  
|[operátor&lt;](#op_lt)|[operátor&lt;&lt;](#op_lt_lt)|[operátor&lt;=](#op_lt_eq)|  
|[Operator ==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>Operator! =  
 Testy nerovnost mezi objekty.  
  
```  
template <class Type, class Other>  
bool operator!=(
    const allocator<Type>& left,  
    const allocator<Other>& right) throw();

template <class T, class Del1, class U, class Del2>  
bool operator!=(
    const unique_ptr<T, Del1>& left,  
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>  
bool operator!=(
    const shared_ptr<Ty1>& left,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Jeden z objektů, které má být testována nerovnost.  
  
 `right`  
 Jeden z objektů, které má být testována nerovnost.  
  
 `Ty1`  
 Typ řízené levé sdílené ukazatele.  
  
 `Ty2`  
 Typ řízené správné sdílené ukazatele.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud objekty nejsou stejné; **false** Pokud objekty jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 První šablona operátor vrací hodnotu false. (Všechny výchozí alokátorů jsou stejné.)  
  
 Druhý a třetí šablony operátory vrátit `!(left == right)`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// memory_op_me.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   allocator<double> Alloc;  
   vector <char>:: allocator_type v1Alloc;  
  
   if ( Alloc != v1Alloc )  
      cout << "The allocator objects Alloc & v1Alloc not are equal."  
           << endl;  
   else  
      cout << "The allocator objects Alloc & v1Alloc are equal."  
           << endl;  
}  
```  
  
```Output  
The allocator objects Alloc & v1Alloc are equal.  
```  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__memory__operator_ne.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()   
    {   
    std::shared_ptr<int> sp0(new int(0));   
    std::shared_ptr<int> sp1(new int(0));   
  
    std::cout << "sp0 != sp0 == " << std::boolalpha   
        << (sp0 != sp0) << std::endl;   
    std::cout << "sp0 != sp1 == " << std::boolalpha   
        << (sp0 != sp1) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
sp0 != sp0 == false  
sp0 != sp1 == true  
```  
  
##  <a name="op_eq_eq"></a>Operator ==  
 Testování rovnosti mezi objekty.  
  
```  
template <class Type, class Other>  
bool operator==(
    const allocator<Type>& left,  
    const allocator<Other>& right) throw();

template <class Ty1, class Del1, class Ty2, class Del2>  
bool operator==(
    const unique_ptr<Ty1, Del1>& left,  
    const unique_ptr<Ty2, Del2>& right);

template <class Ty1, class Ty2>  
bool operator==(
    const shared_ptr<Ty1>& left;,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Jeden z objektů, které má být testována rovnosti.  
  
 `right`  
 Jeden z objektů, které má být testována rovnosti.  
  
 `Ty1`  
 Typ řízené levé sdílené ukazatele.  
  
 `Ty2`  
 Typ řízené správné sdílené ukazatele.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud jsou objekty stejné, `false` Pokud objekty nejsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 První šablona operátor vrací hodnotu true. (Všechny výchozí alokátorů jsou stejné.)  
  
 Druhý a třetí šablony operátory vrátit ` left.get() ==  right.get()`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// memory_op_eq.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   allocator<char> Alloc;  
   vector <int>:: allocator_type v1Alloc;  
  
   allocator<char> cAlloc(Alloc);   
   allocator<int> cv1Alloc(v1Alloc);  
  
   if ( cv1Alloc == v1Alloc )  
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."  
           << endl;  
   else  
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."  
           << endl;  
  
   if ( cAlloc == Alloc )  
      cout << "The allocator objects cAlloc & Alloc are equal."  
           << endl;  
   else  
      cout << "The allocator objects cAlloc & Alloc are not equal."  
           << endl;  
}  
```  
  
```Output  
The allocator objects cv1Alloc & v1Alloc are equal.  
The allocator objects cAlloc & Alloc are equal.  
```  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__memory__operator_eq.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()   
    {   
    std::shared_ptr<int> sp0(new int(0));   
    std::shared_ptr<int> sp1(new int(0));   
  
    std::cout << "sp0 == sp0 == " << std::boolalpha   
        << (sp0 == sp0) << std::endl;   
    std::cout << "sp0 == sp1 == " << std::boolalpha   
        << (sp0 == sp1) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
sp0 == sp0 == true  
sp0 == sp1 == false  
```  
  
##  <a name="op_gt_eq"></a>operátor&gt;=  
 Testy pro jeden objekt je větší než nebo rovna hodnotě druhý objekt.  
  
```  
template <class T, class Del1, class U, class Del2>  
bool operator>=(
    const unique_ptr<T, Del1>& left,  
    const unique_ptr<U, Del2>& right);

template <class Ty1, class Ty2>  
bool operator>=(
    const shared_ptr<Ty1>& left,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Jeden z objektů, který se má porovnat.  
  
 `right`  
 Jeden z objektů, který se má porovnat.  
  
 `Ty1`  
 Typ řízené levé sdílené ukazatele.  
  
 `Ty2`  
 Typ řízené správné sdílené ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí operátory šablony `left.get() >= right.get()`.  
  
##  <a name="op_lt"></a>operátor&lt;  
 Testy pro jeden objekt vrácení menší než druhý objekt.  
  
```  
template <class T, class Del1, class U, class Del2>  
bool operator<(
    const unique_ptr<T, Del1>& left,  
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>  
bool operator<(
    const shared_ptr<Ty1>& left,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Jeden z objektů, který se má porovnat.  
  
 `right`  
 Jeden z objektů, který se má porovnat.  
  
 `Ty1`  
 Typ řízené levém ukazatele.  
  
 `Ty2`  
 Typ řízené správné ukazatele.  
  
##  <a name="op_lt_eq"></a>operátor&lt;=  
 Testy pro jeden objekt je menší než nebo rovna hodnotě druhý objekt.  
  
```  
template <class T, class Del1, class U, class Del2>  
bool operator<=(
    const unique_ptr<T, Del1>& left,  
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>  
bool operator<=(
    const shared_ptr<Ty1>& left,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Jeden z objektů, který se má porovnat.  
  
 `right`  
 Jeden z objektů, který se má porovnat.  
  
 `Ty1`  
 Typ řízené levé sdílené ukazatele.  
  
 `Ty2`  
 Typ řízené správné sdílené ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí operátory šablony`left.get() <= right.get()`  
  
##  <a name="op_gt"></a>operátor&gt;  
 Testy pro jeden objekt, která je větší než druhý objekt.  
  
```  
template <class Ty1, class Del1, class Ty2, class Del2>  
bool operator>(
    const unique_ptr<Ty1, Del1>& left,  
    const unique_ptr<Ty2&, Del2gt;& right);

template <class Ty1, class Ty2>  
bool operator>(
    const shared_ptr<Ty1>& left,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Jeden z objektů, který se má porovnat.  
  
 `right`  
 Jeden z objektů, který se má porovnat.  
  
 `Ty1`  
 Typ řízené levé sdílené ukazatele.  
  
 `Ty2`  
 Typ řízené správné sdílené ukazatele.  
  
##  <a name="op_lt_lt"></a>operátor&lt;&lt;  
Sdílené ukazatele zapíše do datového proudu.  
  
```  
template <class Elem, class Tr, class Ty>  
std::basic_ostream<Elem, Tr>& operator<<(std::basic_ostream<Elem, Tr>& out,  
    shared_ptr<Ty>& sp);
```  
  
### <a name="parameters"></a>Parametry  
 `Elem`  
 Typ elementu datového proudu.  
  
 `Tr`  
 Typ vlastnosti element datového proudu.  
  
 `Ty`  
 Typ řízené sdílené ukazatele.  
  
 `out`  
 Výstupní datový proud  
  
 `sp`  
 Sdílené ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí `out << sp.get()`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__memory__operator_sl.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()   
    {   
    std::shared_ptr<int> sp0(new int(5));   
  
    std::cout << "sp0 == " << sp0 << " (varies)" << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
sp0 == 3f3040 (varies)  
```  
  
## <a name="see-also"></a>Viz také  
 [\<paměť >](../standard-library/memory.md)

