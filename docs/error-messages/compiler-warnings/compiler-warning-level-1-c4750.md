---
title: Kompilátoru (úroveň 1) upozornění C4750 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4750
dev_langs:
- C++
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ffe378f8d2466e702c90127e44f3b48831abf50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4750"></a>C4750 kompilátoru upozornění (úroveň 1)
"identifikátor": funkce s _alloca() vložená do smyčky  
  
 Funkce "identifikátor" vynutí vložené rozšíření [_alloca –](../../c-runtime-library/reference/alloca.md) funkce v rámci smyčku, což by mohlo způsobit k přetečení zásobníku při smyčky.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že funkce "identifikátor" se nemění se [__forceinline](../../cpp/inline-functions-cpp.md) specifikátor.  
  
2.  Ujistěte se, zda neobsahuje funkce "identifikátor" [_alloca –](../../c-runtime-library/reference/alloca.md) funkce, který je obsažen ve smyčce.  
  
3.  Nezadávejte [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/Ox](../../build/reference/ox-full-optimization.md), nebo [/Og](../../build/reference/og-global-optimizations.md) kompilace přepínače.  
  
4.  Místo [_alloca –](../../c-runtime-library/reference/alloca.md) fungovat v [zkuste-except – příkaz](../../cpp/try-except-statement.md) který zachytí k přetečení zásobníku.  
  
## <a name="example"></a>Příklad  
 Následující kód například volání `MyFunction` ve smyčce, a `MyFunction` volání `_alloca` funkce. `__forceinline` Modifikátor způsobí, že rozšíření vložené `_alloca` funkce.  
  
```  
// c4750.cpp  
// compile with: /O2 /W1 /c  
#include <intrin.h>  
  
char * volatile newstr;  
  
__forceinline void myFunction(void) // C4750 warning  
{  
// The _alloca function does not require a __try/__except   
// block because the example uses compiler option /c.  
    newstr = (char * volatile) _alloca(1000);  
}  
  
int main(void)  
{  
    for (int i=0; i<50000; i++)  
       myFunction();  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [_alloca](../../c-runtime-library/reference/alloca.md)