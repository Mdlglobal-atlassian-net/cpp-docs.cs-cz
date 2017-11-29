---
title: "is_volatile – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_volatile
dev_langs: C++
helpviewer_keywords:
- is_volatile class
- is_volatile
ms.assetid: 54922e8a-db4e-4cae-8931-b3352f0b8d3b
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7fc82c86dd5f776ed5b45509c1fc9a3b3193162c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="isvolatile-class"></a>is_volatile – třída
Testy, pokud je typ volatile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Ty>  
struct is_volatile;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud `Ty` je `volatile-qualified`.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// std__type_traits__is_volatile.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_volatile<trivial> == " << std::boolalpha   
        << std::is_volatile<trivial>::value << std::endl;   
    std::cout << "is_volatile<volatile trivial> == " << std::boolalpha   
        << std::is_volatile<volatile trivial>::value << std::endl;   
    std::cout << "is_volatile<int> == " << std::boolalpha   
        << std::is_volatile<int>::value << std::endl;   
    std::cout << "is_volatile<volatile int> == " << std::boolalpha   
        << std::is_volatile<volatile int>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_volatile<trivial> == false  
is_volatile<volatile trivial> == true  
is_volatile<int> == false  
is_volatile<volatile int> == true  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)   
 [is_const – třída](../standard-library/is-const-class.md)