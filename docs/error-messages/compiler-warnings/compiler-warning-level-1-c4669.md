---
title: "Kompilátoru (úroveň 1) upozornění C4669 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4669
dev_langs: C++
helpviewer_keywords: C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d31e2dc077ed1b86c1e246683736ceb1f827b7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4669"></a>C4669 kompilátoru upozornění (úroveň 1)
'přetypovat': unsafe převod: 'class' je spravované nebo WinRT typ objektu  
  
 Přetypování obsahuje prostředí Windows Runtime nebo spravovaný typ. Kompilátor dokončení přetypování provedením bitové kopie jeden ukazatel na druhý, ale poskytuje žádné další kontrolu. Chcete-li toto upozornění, nepodporují přetypování třídy obsahující spravované členy nebo prostředí Windows Runtime typy.  
  
 Následující ukázka generuje C4669 a ukazuje, jak to opravit:  
  
```  
// C4669.cpp  
// compile with: /clr /W1  
ref struct A {  
   int i;  
   Object ^ pObj;   // remove the managed member to fix the warning  
};  
  
ref struct B {  
   int j;  
};  
  
int main() {  
   A ^ a = gcnew A;  
   B ^ b = reinterpret_cast<B ^>(a);   // C4669  
}  
```