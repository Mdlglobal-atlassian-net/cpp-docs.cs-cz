---
title: "aligned_storage – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::aligned_storage
dev_langs: C++
helpviewer_keywords:
- aligned_storage class
- aligned_storage
ms.assetid: f255e345-1f05-4d07-81e4-017f420839fb
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a10f0ee119eab96e183f77c3e51fe877d31ca5ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="alignedstorage-class"></a>aligned_storage – třída
Vytvoří vhodně zarovnaný typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <std::size_t Len, std::size_t Align>  
struct aligned_storage;  
 
template <std::size_t Len, std::size_t Align = alignment_of<max_align_t>::value>  
using aligned_storage_t = typename aligned_storage<Len, Align>::type;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Len`  
 Velikost objektu.  
  
 `Align`  
 Zarovnání objektu.  
  
## <a name="remarks"></a>Poznámky  
 Typedef člen šablony `type` se jedná o synonymum typu POD s zarovnání `Align` a velikost `Len`. `Align`musí být roven `alignment_of<T>::value` pro nějaký typ `T`, nebo výchozí zarovnání.  
  
## <a name="example"></a>Příklad  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
typedef std::aligned_storage<sizeof (int),   
    std::alignment_of<double>::value>::type New_type;   
int main()   
    {   
    std::cout << "alignment_of<int> == "   
        << std::alignment_of<int>::value << std::endl;   
    std::cout << "aligned to double == "   
        << std::alignment_of<New_type>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
alignment_of<int> == 4  
aligned to double == 8  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)   
 [alignment_of – třída](../standard-library/alignment-of-class.md)
