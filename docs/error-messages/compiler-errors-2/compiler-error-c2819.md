---
title: "C2819 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2819
dev_langs: C++
helpviewer_keywords: C2819
ms.assetid: fcc7762d-cb82-4bb1-a715-0d82da832edf
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 770609ed06fd3e123ce02688e3f091018c9f5444
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2819"></a>C2819 chyby kompilátoru
typ "typ" nemá člena přetížená 'operátor ->.  
  
 Je třeba definovat `operator->()` při použití této operace ukazatele.  
  
 Následující ukázka generuje C2819:  
  
```  
// C2819.cpp  
// compile with: /c  
class A {  
   public:  
      int i;  
};  
  
class B {};  
  
void C(B j) {  
   j->i;   // C2819  
}  
  
class D {  
   A* pA;  
  
   public:  
      A* operator->() {  
         return pA;  
      }  
};  
  
void F(D j) {  
   j->i;  
}  
```  
  
 C2819 může také nastat, pokud používáte [C++ – sémantika zásobníku pro odkazové typy](../../dotnet/cpp-stack-semantics-for-reference-types.md). Následující ukázka generuje C2819:  
  
```  
// C2819_b.cpp  
// compile with: /clr  
ref struct R {  
   void Test() {}  
};  
  
int main() {  
   R r;  
   r->Test();   // C2819  
   r.Test();   // OK  
}  
```