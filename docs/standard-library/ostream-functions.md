---
title: "&lt;ostream –&gt; funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
caps.latest.revision: "15"
manager: ghogen
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 252a178f1ce71c30bdd830811cbce59b22acc791
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltostreamgt-functions"></a>&lt;ostream –&gt; funkce
||||  
|-|-|-|  
|[swap](#swap)|[endl](#endl)|[ukončení](#ends)|  
|[vyprázdnění](#flush)|  
  
##  <a name="endl"></a>endl  
 Ukončí řádku a vyprázdní vyrovnávací paměť.  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& endl(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>Parametry  
 `Elem`  
 Typ elementu.  
  
 `Ostr`  
 Objekt typu `basic_ostream`.  
  
 `Tr`  
 Vlastnosti znak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt typu `basic_ostream`.  
  
### <a name="remarks"></a>Poznámky  
 Volání manipulator `Ostr` **.** [put](../standard-library/basic-ostream-class.md#put)( `Ostr` **.** [widen](../standard-library/basic-ios-class.md#widen)( **'\n'**)) a potom zavolá `Ostr` **.** [vyprázdnění](../standard-library/basic-ostream-class.md#flush). Vrátí `Ostr`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// ostream_endl.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "testing" << endl;  
}  
```  
  
```Output  
testing  
```  
  
##  <a name="ends"></a>ukončení  
 Ukončí řetězec.  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& ends(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>Parametry  
 `Elem`  
 Typ elementu.  
  
 `Ostr`  
 Objekt typu `basic_ostream`.  
  
 `Tr`  
 Vlastnosti znak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt typu `basic_ostream`.  
  
### <a name="remarks"></a>Poznámky  
 Volání manipulator `Ostr` **.** [put](../standard-library/basic-ostream-class.md#put)( `Elem`( **'\0'**)). Vrátí`Ostr.`  
  
### <a name="example"></a>Příklad  
  
```cpp  
// ostream_ends.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "a";  
   cout << "b" << ends;  
   cout << "c" << endl;  
}  
```  
  
```Output  
ab c  
```  
  
##  <a name="flush"></a>vyprázdnění  
 Vyprázdní vyrovnávací paměť.  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& flush(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>Parametry  
 `Elem`  
 Typ elementu.  
  
 `Ostr`  
 Objekt typu `basic_ostream`.  
  
 `Tr`  
 Vlastnosti znak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt typu `basic_ostream`.  
  
### <a name="remarks"></a>Poznámky  
 Volání manipulator `Ostr` **.** [vyprázdnění](../standard-library/basic-ostream-class.md#flush). Vrátí `Ostr`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// ostream_flush.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "testing" << flush;  
}  
```  
  
```Output  
testing  
```  
  
##  <a name="swap"></a>swap  
 Výměny hodnoty dva `basic_ostream` objekty.  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_ostream<Elem, Tr>& left,  
    basic_ostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Odkaz na lvalue `basic_ostream` objektu.  
  
 `right`  
 Odkaz na lvalue `basic_ostream` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony `swap` provede `left.swap(right)`.  
  
## <a name="see-also"></a>Viz také  
 [\<ostream – >](../standard-library/ostream.md)

