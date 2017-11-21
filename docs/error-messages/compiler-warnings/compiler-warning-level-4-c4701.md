---
title: "Kompilátoru (úroveň 4) upozornění C4701 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4701
dev_langs: C++
helpviewer_keywords: C4701
ms.assetid: d7c76c66-1f3f-4d3c-abe4-5d94c84a5a1f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 696e3086f139d70ada9afdf1af02a007cbe1609f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4701"></a>C4701 kompilátoru upozornění (úroveň 4)
Potenciálně Neinicializovaný místní proměnné použít název  
  
 Místní proměnná *název* může použít bez přiřazení hodnotu. To může vést k neočekávaným výsledkům.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří C4701 a C4703.  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr) // C4701 and C4703  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
```Output  
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used  
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used  
  
```  
  
 Chcete-li toto upozornění, inicializace proměnné, jak je znázorněno v tomto příkladu:  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p = nullptr;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr)  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [C4703 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)   
 [Upozornění, SDL a zlepšení Neinicializovaný proměnné detekce](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)