---
title: "remove_cv – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::remove_cv
dev_langs: C++
helpviewer_keywords:
- remove_cv class
- remove_cv
ms.assetid: 8502602a-1c80-479c-84e0-33bd1d6496d6
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c0049a7d71c99e4073a6e045060f92aed6a41cc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="removecv-class"></a>remove_cv – třída
Vytvoří nekonstantní/přechodný typ z typu  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class T>  
struct remove_cv;  
 
template <class T>  
using remove_cv_t = typename remove_cv<T>::type;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, který chcete upravit.  
  
## <a name="remarks"></a>Poznámky  
 Instance `remove_cv<T>` obsahuje upravit – typ, který je `T1` při `T` je ve formátu `const T1`, `volatile T1`, nebo `const volatile T1`, jinak `T`.  
  
## <a name="example"></a>Příklad  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_cv_t<const volatile int> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_cv_t<const volatile int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
remove_cv_t<const volatile int> == int  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)   
 [remove_const – třída](../standard-library/remove-const-class.md)   
 [remove_volatile – třída](../standard-library/remove-volatile-class.md)