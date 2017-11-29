---
title: "Kompilátoru (úroveň 1) upozornění C4803 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4803
dev_langs: C++
helpviewer_keywords: C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 43353a5a86bbd7c8e185fed925506ac1ae0fbfe8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4803"></a>C4803 kompilátoru upozornění (úroveň 1)
"metody": metoda pro vyvolání obsahuje třídu jiného úložiště od události, 'událost'  
  
Metody události musí mít stejnou třídu úložiště jako deklaraci události. Kompilátor upraví metody události tak, že třídy úložiště jsou stejné.  
  
Toto upozornění může dojít, pokud máte třídu, která implementuje událost z rozhraní. Kompilátor implicitně negeneruje vyvolat metodu pro událost v rozhraní. Při implementaci tohoto rozhraní v třídě, kompilátor implicitně generovat vyvolat metodu a že metoda nebude virtuální, proto upozornění. Další informace o událostech najdete v tématu [událostí](../../windows/event-cpp-component-extensions.md).  
  
V tématu [upozornění](../../preprocessor/warning.md) – Direktiva pragma pro informace o tom, jak vypnout upozornění.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4803.  
  
```  
// C4803.cpp  
// compile with: /clr /W1  
using namespace System;  
  
public delegate void Del();  
  
ref struct E {  
   Del ^ _pd1;  
   event Del ^ E1 {  
      void add (Del ^ pd1) {  
         _pd1 = dynamic_cast<Del ^>(Delegate::Combine(_pd1, pd1));  
      }  
  
      void remove(Del^ pd1) {  
         _pd1 = dynamic_cast<Del^> (Delegate::Remove(_pd1, pd1));  
      }  
  
      virtual void raise() {   // C4803 warning (remove virtual)  
         if (_pd1)  
            _pd1();  
      }  
   }  
  
   void func() {  
      Console::WriteLine("In E::func()");  
   }  
};  
  
int main() {  
   E ^ ep = gcnew E;  
   ep->E1 += gcnew Del(ep, &E::func);  
   ep->E1();  
   ep->E1 -= gcnew Del(ep, &E::func);  
   ep->E1();  
}  
```  