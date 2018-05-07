---
title: C2247 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2247
dev_langs:
- C++
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed27398ea1f51ccc2ef0d3339446b422c7a503c0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2247"></a>C2247 chyby kompilátoru
"identifikátor" není dostupný, protože používá 'class'. 'specifikátor' dědění z 'class'.  
  
 `identifier` dědí z třídy deklarovat s privátní nebo chráněného přístupu.  
  
 Následující ukázka generuje C2247:  
  
```  
// C2247.cpp  
class A {  
public:  
   int i;  
};  
class B : private A {};    // B inherits a private A  
class C : public B {} c;   // so even though C's B is public  
int j = c.i;               // C2247, i not accessible  
```  
  
 Tato chyba může být také vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual Studio .NET 2003: přístup k ovládacímu prvku s chráněné členy. Chráněný člen (ne) je přístupné pouze prostřednictvím funkce člena třídy (B), která dědí z třídy (A), jehož (ne) je členem.  
  
 Kód, který je platná v sadě Visual Studio .NET 2003 a sady Visual Studio .NET verzí aplikace Visual C++ deklarujte člen být friend typu. Veřejné dědičnost může také použít.  
  
```  
// C2247b.cpp  
// compile with: /c  
// C2247 expected  
class A {  
public:  
   void f();  
   int n;  
};  
  
class B: protected A {  
   // Uncomment the following line to resolve.  
   // friend void A::f();  
};  
  
void A::f() {  
   B b;  
   b.n;  
}  
```  
  
 V důsledku kompilátoru shoda práci, kterou bylo provedeno pro Visual Studio .NET 2003 lze také generovat C2247: privátní základní třídy teď nedostupné. Třída (A), která je privátní základní třída pro typ (B) musí není přístupný na typ (C) který se používá jako základní třída B.  
  
 Kód, který je platná v sadě Visual Studio .NET 2003 a sady Visual Studio .NET verzí aplikace Visual C++ použijte operátor rozsahu.  
  
```  
// C2247c.cpp  
// compile with: /c  
struct A {};  
  
struct B: private A {};  
  
struct C : B {  
   void f() {  
      A *p1 = (A*) this;   // C2247  
      // try the following line instead  
      // ::A *p2 = (::A*) this;  
   }  
};  
```