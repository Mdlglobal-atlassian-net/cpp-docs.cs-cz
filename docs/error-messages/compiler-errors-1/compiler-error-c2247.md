---
title: Chyba kompilátoru C2247
ms.date: 11/04/2016
f1_keywords:
- C2247
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
ms.openlocfilehash: e82b406b20d77a824b62207b1766fec55ac65c5c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758902"
---
# <a name="compiler-error-c2247"></a>Chyba kompilátoru C2247

identifikátor není přístupný, protože třída používá specifikátor pro dědění z třídy.

`identifier` se dědí ze třídy deklarované pomocí privátního nebo chráněného přístupu.

Následující ukázka generuje C2247:

```cpp
// C2247.cpp
class A {
public:
   int i;
};
class B : private A {};    // B inherits a private A
class C : public B {} c;   // so even though C's B is public
int j = c.i;               // C2247, i not accessible
```

Tato chyba se může vygenerovat taky v důsledku práce s shodami s kompilátorem, která se dokončila pro Visual Studio .NET 2003: řízení přístupu s chráněnými členy. K chráněnému členu (n) lze přistupovat pouze prostřednictvím členské funkce třídy (B), která dědí z třídy (A), ze které je (n) členem.

Pro kód, který je platný jak v rámci Visual Studio .NET 2003, tak ve verzi Visual Studio C++.NET, deklarujte člena jako přítele typu. Lze také použít dědění typu public.

```cpp
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

C2247 lze také vygenerovat v důsledku práce s vyhovujícími kompilátory, které byly provedeny pro Visual Studio .NET 2003: soukromé základní třídy jsou nyní nedostupné. Třída (A), která je soukromou základní třídou typu (B), by neměla být přístupná pro typ (C), který používá B jako základní třídu.

Pro kód, který je platný jak v jazyce Visual Studio .NET 2003, tak ve verzi Visual Studio C++.NET, použijte operátor Scope.

```cpp
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
