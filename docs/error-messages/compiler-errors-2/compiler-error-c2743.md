---
title: "C2743 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2743
dev_langs:
- C++
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29826dde6b9f92dd01e3a6420eed0d836660121f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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