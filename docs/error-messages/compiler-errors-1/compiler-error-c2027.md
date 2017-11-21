---
title: "C2027 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2027
dev_langs: C++
helpviewer_keywords: C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a2fec9194858127ca08ecc0a891a81a91de48fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2027"></a>C2027 chyby kompilátoru
použití nedefinované typu "typ"  
  
 Typ nelze použít, dokud nebude definováno. Chcete-li vyřešit chyby, ujistěte se, že typ je plně definována před odkazující na ho.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2027.  
  
```  
// C2027.cpp  
class C;  
class D {  
public:  
   void func() {  
   }  
};  
  
int main() {  
   C *pC;  
   pC->func();   // C2027  
  
   D *pD;  
   pD->func();  
}  
```  
  
## <a name="example"></a>Příklad  
 Je možné deklarovat ukazatel typu deklarovaný ale definován.  Ale Visual C++ nepovoluje odkaz na nedefinovaný typu.  
  
 Následující ukázka generuje C2027.  
  
```  
// C2027_b.cpp  
class A;  
A& CreateA();  
  
class B;  
B* CreateB();  
  
int main() {  
   CreateA();   // C2027  
   CreateB();   // OK  
}  
```