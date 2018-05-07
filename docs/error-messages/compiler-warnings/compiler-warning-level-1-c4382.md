---
title: Kompilátoru (úroveň 1) upozornění C4382 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4382
dev_langs:
- C++
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c02f0cb2d22aebb9af31844aec3bf68b97c3442e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4382"></a>C4382 kompilátoru upozornění (úroveň 1)
vyvolání 'type': typ s __clrcall – destruktor nebo kopírovacího konstruktoru pouze zachytit v/CLR: pure modulu  
  
 **/CLR: pure** – možnost kompilátoru je zastaralá ve Visual Studiu 2015.  
  
 Když kompilujete s **/CLR** (není **/CLR: pure**), zpracování výjimek v nativním typu být očekává členské funkce [__cdecl](../../cpp/cdecl.md) a není [__clrcall](../../cpp/clrcall.md). Nativní typy s členské funkce pomocí `__clrcall` konvence volání nemůže být zachycena v modulu kompilovat s **/CLR**.  
  
 Pokud se výjimka zachycena v modulu kompilovat s **/CLR: pure**, můžete toto upozornění ignorovat.  
  
 Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4382.  
  
```  
// C4382.cpp  
// compile with: /clr /W1 /c  
struct S {  
   __clrcall ~S() {}  
};  
  
struct T {  
   ~T() {}  
};  
  
int main() {  
   S s;  
   throw s;   // C4382  
  
   S * ps = &s;  
   throw ps;   // OK  
  
   T t;  
   throw t;   // OK  
}  
```