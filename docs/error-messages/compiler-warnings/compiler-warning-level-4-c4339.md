---
title: Kompilátoru (úroveň 4) upozornění C4339 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4339
dev_langs:
- C++
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b94d6a059c1c04eeae04bf917a84836c0354197e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4339"></a>C4339 kompilátoru upozornění (úroveň 4)
'type': použití nedefinované typu zjistil v WinRT nebo CLR meta-data - použití tohoto typu může vést k výjimku modulu runtime  
  
 Typ není definovaný v kódu, který byl sestaven pro prostředí Windows Runtime nebo modul common language runtime. Definování typu předejdete výjimku možné modulu runtime.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Následující ukázka generuje C4339 a ukazuje, jak to opravit:  
  
```  
// C4339.cpp  
// compile with: /W4 /clr /c  
// C4339 expected  
#pragma warning(default : 4339)  
  
// Delete the following line to resolve.  
class A;  
  
// Uncomment the following line to resolve.  
// class A{};  
  
class X {  
public:  
   X() {}  
  
   virtual A *mf() {  
      return 0;  
   }  
};  
  
X * f() {  
   return new X();  
}  
```