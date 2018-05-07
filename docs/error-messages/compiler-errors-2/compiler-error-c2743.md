---
title: C2743 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2743
dev_langs:
- C++
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a762a7c816f713f9371ff50524ccb582753535b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2743"></a>C2743 chyby kompilátoru
'type': nelze catch nativního typu s __clrcall – destruktor nebo kopírovací konstruktor  
  
 Modul kompilován s **/CLR** pokus o zachycení výjimek nativní typu a kde je typ destruktor nebo kopírovacího konstruktoru používá `__clrcall` konvence volání.  
  
 Když kompilujete s **/CLR**, zpracování výjimek v nativním typu být očekává členské funkce [__cdecl](../../cpp/cdecl.md) a není [__clrcall](../../cpp/clrcall.md). Nativní typy s členské funkce pomocí `__clrcall` konvence volání nemůže být zachycena v modulu kompilovat s **/CLR**.  
  
 Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2743.  
  
```  
// C2743.cpp  
// compile with: /clr  
public struct S {  
   __clrcall ~S() {}  
};  
  
public struct T {  
   ~T() {}  
};  
  
int main() {  
   try {}  
   catch(S) {}   // C2743  
   // try the following line instead  
   // catch(T) {}  
  
   try {}  
   catch(S*) {}   // OK  
}  
```