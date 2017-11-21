---
title: "C3145 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3145
dev_langs: C++
helpviewer_keywords: C3145
ms.assetid: f165c874-0f51-45c7-85e8-ebe321cbc168
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6b6548d04d701cb510669d91780979951c485685
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3145"></a>C3145 chyby kompilátoru
'objekt': globální nebo statické proměnné nemusí být spravovaná nebo WinRT typu "typ"  
  
 Mohou definovat pouze CLR nebo WinRT objektů v rámci oboru funkce.  
  
 Následující ukázka generuje C3145 a ukazuje, jak to opravit:  
  
```  
// C3145.cpp  
// compile with: /clr  
using namespace System;   
ref class G {};   
  
G ^ ptr;   // C3145  
G ^ ptr2 = gcnew G;   // C3145  
  
ref class GlobalObjects {  
public:  
   static G ^ ptr;   // OK  
   static G ^ ptr2 = gcnew G;   // OK   
};   
  
int main() {  
   G ^ ptr;   // OK  
   G ^ ptr2 = gcnew G;   // OK  
}  
```  
  
 Následující ukázka generuje C3145:  
  
```  
// C3145b.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   static int data;  
};  
  
interior_ptr<int> p = &(MyClass::data);   // C3145  
  
void Test(interior_ptr<int> x) {}  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;  
   interior_ptr<int> p = &(h_MyClass->data);  
}  
```  
