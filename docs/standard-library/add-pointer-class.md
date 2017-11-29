---
title: "add_pointer – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::add_pointer
dev_langs: C++
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c8a55af99a2a058c967ad87dadb038ce06cf56b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="addpointer-class"></a>add_pointer – třída
Vytvoří ukazatel na typ z určeného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class T>  
struct add_pointer;  
 
template <class T>
using add_pointer_t = typename add_pointer<T>::type;  
```  
  
#### <a name="parameters"></a>Parametry  
*T*  
Typ, který chcete upravit.  
  
## <a name="remarks"></a>Poznámky  
Typedef člen `type` názvy stejného typu jako `remove_reference<T>::type*`. Alias `add_pointer_t` je zástupce pro přístup k typedef člen `type`.  
  
Protože je neplatné. Chcete-li ukazatel z odkaz, `add_pointer` odebere odkaz, pokud existuje, ze zadaného typu dříve, než se provede ukazatel na type. V důsledku toho můžete použít typ s `add_pointer` bez se problémem o tom, zda typu odkaz.  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje, který `add_pointer` typu je stejný jako ukazatel na typu.  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
{   
    std::add_pointer_t<int> *p = (int **)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_pointer_t<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
add_pointer_t<int> == int *  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)   
 [remove_pointer – třída](../standard-library/remove-pointer-class.md)