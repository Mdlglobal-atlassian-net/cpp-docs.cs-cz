---
title: "C2064 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2064
dev_langs: C++
helpviewer_keywords: C2064
ms.assetid: 6cda05da-f437-4f50-9813-ae69538713a3
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e0c82ae2de90a6e4e6e7e66648d84c2b55a9c2b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2064"></a>C2064 chyby kompilátoru
Výraz nelze vyhodnotit funkci trvá N argumenty  
  
 Při volání funkce prostřednictvím výrazu. Výraz nebyl vyhodnocen jako ukazatel na funkci, která provede zadaný počet argumentů.  
  
 V tomto příkladu kód pokusí volat jiné funkce jako funkce. Následující ukázka generuje C2064:  
  
```  
// C2064.cpp  
int i, j;  
char* p;  
void func() {  
   j = i();    // C2064, i is not a function  
   p();        // C2064, p doesn't point to a function  
}  
```  
  
 Ukazatele na nestatické členské funkce musí volat v kontextu instance objektu. Následující ukázka generuje C2064 a ukazuje, jak to opravit:  
  
```  
// C2064b.cpp  
struct C {  
   void func1(){}  
   void func2(){}  
};  
  
typedef void (C::*pFunc)();  
  
int main() {  
   C c;  
   pFunc funcArray[2] = {&C::func1, &C::func2};  
   (funcArray[0])();    // C2064   
   (c.*funcArray[0])(); // OK - function called in instance context  
}  
  
```  
  
 V rámci třídy ukazatelů na funkce člena musí také označovat volání kontextu objektu. Následující ukázka generuje C2064 a ukazuje, jak to opravit:  
  
```  
// C2064d.cpp  
// Compile by using: cl /c /W4 C2064d.cpp  
struct C {  
   typedef void (C::*pFunc)();  
   pFunc funcArray[2];  
   void func1(){}  
   void func2(){}  
   C() {  
      funcArray[0] = &C::func1;  
      funcArray[1] = &C::func2;  
   }  
   void func3() {  
      (funcArray[0])();   // C2064  
      (this->*funcArray[0])(); // OK - called in this instance context  
   }  
};  
```