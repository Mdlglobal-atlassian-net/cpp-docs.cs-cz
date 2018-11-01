---
title: Kompilátor upozornění (úroveň 2) C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: 8baf3c03c87dc70a80b785d7f81cbee4e1d828f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454857"
---
# <a name="compiler-warning-level-2-c4250"></a>Kompilátor upozornění (úroveň 2) C4250

'class1': 'class2::member"prostřednictvím dominance dědí

Dva nebo více členů mají stejný název. V `class2` se dědí, protože je základní třídou pro jiné třídy, které tento člen.

Chcete-li potlačit C4250, použijte [upozornění](../../preprocessor/warning.md) direktivy pragma.

Vzhledem k tomu, že virtuální základní třídy je sdílen mezi více odvozených tříd, název v odvozené třídě dominuje název v základní třídě. Například s ohledem následující hierarchie tříd, existují dvě definice func zděděné v rámci kosočtverce: instance vbc::func() prostřednictvím slabé třídy a dominantní:: func() prostřednictvím dominantní třídy. Neúplného volání func() prostřednictvím objekt třídy kosočtverce vždy volá instance dominate:: func().  Kdyby zavést instance func() slabé třídy ani definice by převládají na poli a volání by být označeno jako dvojznačné.

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

Tento příklad ukazuje mnohem složitější situace. Následující ukázka generuje C4250.

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