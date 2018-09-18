---
title: Chyba kompilátoru C2247 | Dokumentace Microsoftu
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
ms.openlocfilehash: f00516a3aa9cb2e88f47e81ad27890247a725733
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107464"
---
# <a name="compiler-error-c2247"></a>Chyba kompilátoru C2247

'identifier' není dostupné, protože 'class' používá "specifikátor" dědit z 'class'

`identifier` se dědí z třídy deklarované jako s přístupem k soukromé nebo chráněné.

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

Tato chyba může být také generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual Studio .NET 2003: přístup k ovládacím prvkem chráněné členy. Chráněný člen (n) je přístupný pouze prostřednictvím funkce člena třídy (B), která dědí z třídy (A) je (n) je jejím členem.

Pro kód, který je platný v aplikaci Visual Studio .NET 2003 a Visual Studio .NET verzí jazyka Visual C++ deklarujte člen, který chcete být funkce friend typu. Možné využít také dědění typu public.

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

C2247 může být také generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual Studio .NET 2003: soukromé základní třídy nyní nedostupná. Třídu (A), která je na typ soukromé základní třídu (B) by se neměly přístupné pro typ (C), který používá jako základní třída B.

Pro kód, který je platný v aplikaci Visual Studio .NET 2003 a Visual Studio .NET verzí jazyka Visual C++ použijte operátor rozsahu.

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