---
title: Kompilátor upozornění (úroveň 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: 231482547856fc07d43ecfb859b31c2ece49fc5e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776489"
---
# <a name="compiler-warning-level-4-c4487"></a>Kompilátor upozornění (úroveň 4) C4487

'derived_class_function': odpovídá zděděnou nevirtuální metodu "base_class_function", ale není explicitně označené jako new.

Funkce v odvozené třídě nemá stejný podpis jako funkci nevirtuální základní třídy. C4487 upozorňuje, že odvozené třídy funkce nemůže přepsat funkci základní třídy. Explicitně označit funkce odvozené třídy jako `new` vyřešit tato upozornění.

Další informace najdete v tématu [new (nový slot v tabulce vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4487.

```
// C4487.cpp
// compile with: /W4 /clr
using namespace System;
public ref struct B {
   void f() { Console::WriteLine("in B::f"); }
   void g() { Console::WriteLine("in B::g"); }
};

public ref struct D : B {
   void f() { Console::WriteLine("in D::f"); }   // C4487
   void g() new { Console::WriteLine("in D::g"); }   // OK
};

int main() {
   B ^ a = gcnew D;
   // will call base class functions
   a->f();
   a->g();
}
```