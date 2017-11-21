---
title: "Extent – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::extent
dev_langs: C++
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 185cb6108801b31c19301a0f7488352a6948f5bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="extent-class"></a>extent – třída
Získá rozměru pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Ty, unsigned I = 0>  
struct extent;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
 `I`  
 Pole vázán k dotazu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `Ty` je typ pole, která má nejméně `I` dimenze typu dotaz obsahuje počet elementů v dimenzi určeného `I`. Pokud `Ty` není typu pole nebo je jeho pořadí menší než `I`, nebo pokud `I` rovná nule a `Ty` je typu "pole Neznámý hranice elementu `U`", typ dotazu obsahuje hodnotu 0.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// std__type_traits__extent.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "extent 0 == "   
        << std::extent<int[5][10]>::value << std::endl;   
    std::cout << "extent 1 == "   
        << std::extent<int[5][10], 1>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
extent 0 == 5  
extent 1 == 10  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)   
 [remove_all_extents – třída](../standard-library/remove-all-extents-class.md)   
 [remove_extent – třída](../standard-library/remove-extent-class.md)
