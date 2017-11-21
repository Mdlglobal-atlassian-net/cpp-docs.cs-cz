---
title: "Kompilátoru (úroveň 1) upozornění C4927 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4927
dev_langs: C++
helpviewer_keywords: C4927
ms.assetid: 7009e740-a2ef-4130-96ba-482e092f717a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ef83c97d45a614738f08764ef25d0714832da313
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4927"></a>C4927 kompilátoru upozornění (úroveň 1)
Neplatný převod; implicitně použilo více než jeden uživatelem definovaný převod  
  
 Více než jeden uživatelem definovaný převod implicitně platí pro jednu hodnotu – kompilátor nenalezl explicitní převod ale nalézt převodu, který se používá.  
  
 Následující ukázka generuje C4927:  
  
```  
// C4927.cpp  
// compile with: /W1  
struct B  
{  
   operator int ()  
   {  
      return 0;  
   }  
};  
  
struct A  
{  
   A(int i)  
   {  
   }  
  
   /*  
   // uncomment this constructor to resolve  
   A(B b)  
   {  
   }  
   */  
};  
  
A f1( B& b)  
{  
   return A(b);  
}  
  
B& f2( B& b)  
{  
   return b;  
}  
  
A f()  
{  
   B b;  
   return A(b);   // ok  
   return f1(b);  // ok  
   return b;      // C4927  
   return B(b);   // C4927  
   return f2(b);  // C4927  
}  
  
int main()  
{  
   B b;  
   A a = b;  
   A a2(b);  
}  
```