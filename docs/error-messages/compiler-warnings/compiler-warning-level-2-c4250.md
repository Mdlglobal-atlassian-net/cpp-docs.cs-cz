---
title: Upozornění kompilátoru (úroveň 2) C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: e0feb1cb7131b4388c87213a85ff1c921f636e1b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162033"
---
# <a name="compiler-warning-level-2-c4250"></a>Upozornění kompilátoru (úroveň 2) C4250

' Class1 ': dědí z ' Class2:: member ' prostřednictvím dominantního postavení

Dva nebo více členů mají stejný název. Objekt ve `class2` je zděděn, protože se jedná o základní třídu pro ostatní třídy, které tento člen obsahovaly.

Chcete-li potlačit C4250, použijte direktivu pragma [Warning](../../preprocessor/warning.md) .

Vzhledem k tomu, že virtuální základní třída je sdílena mezi více odvozenými třídami, název v odvozené třídě slouží jako název v základní třídě. Například vzhledem k následující hierarchii tříd jsou v rámci kosočtverce zděděny dvě definice Func: instance Vbc:: Func () prostřednictvím slabé třídy a dominantního typu: Func () prostřednictvím dominantní třídy. Nekvalifikované volání funkce Func () prostřednictvím objektu Diamond Class vždycky zavolá instanci dominantního prvku:: Func ().  Pokud byla slabá třída zavedena instance Func (), ani žádná definice by nevedla, a volání by bylo označeno jako nejednoznačné.

```cpp
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

```cpp
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

Tato ukázka ukazuje složitější situaci. Následující ukázka generuje C4250.

```cpp
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
