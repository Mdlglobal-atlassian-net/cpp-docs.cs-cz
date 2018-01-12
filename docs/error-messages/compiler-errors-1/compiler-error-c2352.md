---
title: "C2352 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2352
dev_langs: C++
helpviewer_keywords: C2352
ms.assetid: 0efad8cb-659f-4b3e-8f6f-9f8ec44d345c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f78b68103586a7ee5b73a73b2d14e188aabc46ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2352"></a>C2352 chyby kompilátoru
'class::function': Neplatné volání nestatické členské funkce  
  
 A `static` – členská funkce volá nestatické členské funkce. Nebo nestatické členské funkce byla volána mimo třídu jako statické funkce.  
  
 Následující ukázka generuje C2352 a ukazuje, jak to opravit:  
  
```  
// C2352.cpp  
// compile with: /c  
class CMyClass {  
public:  
   static void func1();  
   void func2();  
   static void func3() {  
      func2();   // C2352 calls nonstatic func2  
      func1();   // OK calls static func1  
   }  
};  
```  
  
 Následující ukázka generuje C2352 a ukazuje, jak to opravit:  
  
```  
// C2352b.cpp  
class MyClass {  
public:  
   void MyFunc() {}  
   static void MyFunc2() {}  
};  
  
int main() {  
   MyClass::MyFunc();   // C2352  
   MyClass::MyFunc2();   // OK  
}  
```