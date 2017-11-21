---
title: alignof a alignas (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cf1c32b406c0a315373b379dacab78ea41b5dbf6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="alignof-and-alignas-c"></a>alignof a alignas (C++)
`alignas` Specifikátor typu je přenosné, C++ standardní způsob, jak určit vlastní zarovnání proměnných a uživatelem definované typy. `alignof` Operátor je podobně standardní, přenosný způsob, jak získat zarovnání zadaného typu nebo proměnné.  
  
## <a name="example"></a>Příklad  
 Můžete použít `alignas` na třídu, naráženém nebo union, nebo na jednotlivé členy. Když více `alignas` došlo k specifikátory, kompilátor vybere ten nejpřísnějším (jeden s největší hodnotou).  
  
```cpp  
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar  
{      
    int i;       // 4 bytes  
    int n;      // 4 bytes  
    alignas(4) char arr[3];  
    short s;          // 2 bytes  
};  

int main()
{  
    std::cout << alignof(Bar) << std::endl; // output: 16  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Zarovnání](../cpp/alignment-cpp-declarations.md)