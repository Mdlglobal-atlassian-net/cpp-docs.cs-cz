---
title: "Kompilátoru (úroveň 4) upozornění C4913 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4913
dev_langs: C++
helpviewer_keywords: C4913
ms.assetid: b94aa52e-6029-4170-9134-017714931546
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 71e9021e91f98b2d6b6e90590d964056cf562f69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4913"></a>C4913 kompilátoru upozornění (úroveň 4)
**uživatel definované binární operátor ',' existuje, ale žádné přetížení může převést všechny operandy, výchozí integrovanou binární operátor ',' použité**  
  
 Volání operátor předdefinované čárky došlo k chybě programu, který také měl operátor přetížené čárkami; nebyla převodu, který jste myšlenku mohlo dojít.  
  
 Následující ukázka kódu generuje C4913:  
  
```  
// C4913.cpp  
// compile with: /W4  
struct A  
{  
};  
  
struct S  
{  
};  
  
struct B  
{  
   // B() { }  
   // B(S &s) { s; }  
};  
  
B operator , (A a, B b)     
{  
   a;  
   return b;  
}  
  
int main()  
{  
   A a;  
   B b;  
   S s;  
  
   a, b;   // OK calls user defined operator  
   a, s;   // C4913 uses builtin comma operator  
           // uncomment the conversion code in B to resolve.  
}  
```