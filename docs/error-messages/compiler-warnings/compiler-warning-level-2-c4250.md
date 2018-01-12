---
title: "Kompilátoru (úroveň 2) upozornění C4250 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4250
dev_langs: C++
helpviewer_keywords: C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d92a337e3ded4b958bb9d1dbb7359d21f28d619c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4250"></a>C4250 kompilátoru upozornění (úroveň 2)
"třída1": dědí 'class2::member' prostřednictvím dominance  
  
 Dvě nebo více členů mají stejný název. V `class2` je zděděn, protože je základní třída pro třídy, které obsahovaly tohoto člena.  
  
 Chcete-li potlačit C4250, použijte [upozornění](../../preprocessor/warning.md) – Direktiva pragma.  
  
 Vzhledem k tomu, že virtuální základní třídy je sdílen více odvozené třídy, název v odvozené třídě dominuje název v základní třídě. Například následující hierarchie tříd zadána existují dvě definice func převzít v rámci kosočtverec: instance vbc::func() prostřednictvím slabé třídy a dominantní:: func() prostřednictvím dominantní třídy. Nekvalifikované volání func() prostřednictvím objekt třídy kosočtverec vždy volá dominate:: func() instance.  Kdyby zavádět instanci func() slabé třídy ani definice převažovalo a volání by označeno jako dvojznačné.  
  
```  
// C4250.cpp  
// compile with: /c /W2  
#include <stdio.h>  
struct vbc {  
   virtual void func() { printf("vbc::func\n"); }  
};  
  
struct weak : public virtual vbc {};  
  
struct dominant : public virtual vbc {  
   void func() { printf("dominant::func\n"); }  
};  
  
struct diamond : public weak, public dominant {};  
  
int main() {  
   diamond d;  
   d.func();   // C4250  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4250.  
  
```  
// C4250_b.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
using namespace std;  
class A {  
public:  
   virtual operator int () {  
      return 2;  
   }  
};  
  
class B : virtual public A {  
public:  
   virtual operator int () {  
      return 3;  
   }  
};  
  
class C : virtual public A {};  
  
class E : public B, public C {};   // C4250  
  
int main() {  
   E eObject;  
   cout << eObject.operator int() << endl;  
}  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje složitější situaci. Následující ukázka generuje C4250.  
  
```  
// C4250_c.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
using namespace std;  
  
class V {  
public:  
   virtual int f() {  
      return 1024;  
   }  
};  
  
class B : virtual public V {  
public:  
   int b() {  
      return f(); // B::b() calls V::f()  
   }  
};  
  
class M : virtual public V {  
public:  
   int f() {  
      return 7;  
   }  
};  
  
// because of dominance, f() is M::f() inside D,  
// changing the meaning of B::b's f() call inside a D  
class D : public B, public M {};   // C4250  
  
int main() {  
   D d;  
   cout << "value is: " << d.b();   // invokes M::f()  
}  
```