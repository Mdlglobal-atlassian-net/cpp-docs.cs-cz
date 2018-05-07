---
title: __noop | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __noop_cpp
- __noop
dev_langs:
- C++
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14d7ab3f1a61dc0644bf5683376ac676fbfcd6b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="noop"></a>__noop
**Konkrétní Microsoft**  
  
 `__noop` Vnitřní Určuje, že by měl být ignorovány funkci a analyzovat seznam argumentů, ale žádný kód vygenerování pro argumenty. Je určený pro použití v globální ladění funkcí, které přijímají proměnný počet argumentů.  
  
 Kompilátor převede `__noop` vnitřní na 0 v době kompilace.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak můžete použít `__noop`.  
  
```  
// compiler_intrinsics__noop.cpp  
// compile with or without /DDEBUG  
#include <stdio.h>  
  
#if DEBUG  
   #define PRINT   printf_s  
#else  
   #define PRINT   __noop  
#endif  
  
int main() {  
   PRINT("\nhello\n");  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)