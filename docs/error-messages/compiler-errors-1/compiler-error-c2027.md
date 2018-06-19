---
title: C2027 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2027
dev_langs:
- C++
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be3c85d2ffbd3fffe4e1e6ce6dafc615f199c00a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167441"
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