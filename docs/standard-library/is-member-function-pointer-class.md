---
title: "is_member_function_pointer – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_member_function_pointer
dev_langs: C++
helpviewer_keywords:
- is_member_function_pointer class
- is_member_function_pointer
ms.assetid: 02e372c4-2714-40f2-b376-2e10ca91c8ed
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bc816e84542ac393d47771ba8f529e9c6261ee5b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ismemberfunctionpointer-class"></a>is_member_function_pointer – třída
Testy, pokud je typ ukazatele na člena funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Ty>  
struct is_member_function_pointer;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` ukazatel do funkce člen nebo `cv-qualified` ukazatel členské funkce, jinak má hodnotu false.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// std__type_traits__is_member_function_pointer.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct functional   
    {   
    int f();   
    };   
  
int main()   
    {   
    std::cout << "is_member_function_pointer<trivial *> == "   
        << std::boolalpha   
        << std::is_member_function_pointer<trivial *>::value   
        << std::endl;   
    std::cout << "is_member_function_pointer<int trivial::*> == "   
        << std::boolalpha   
        << std::is_member_function_pointer<int trivial::*>::value   
        << std::endl;   
    std::cout << "is_member_function_pointer<int (functional::*)()> == "   
        << std::boolalpha   
        << std::is_member_function_pointer<int (functional::*)()>::value   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_member_function_pointer<trivial *> == false  
is_member_function_pointer<int trivial::*> == false  
is_member_function_pointer<int (functional::*)()> == true  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)   
 [is_member_pointer – třída](../standard-library/is-member-pointer-class.md)
