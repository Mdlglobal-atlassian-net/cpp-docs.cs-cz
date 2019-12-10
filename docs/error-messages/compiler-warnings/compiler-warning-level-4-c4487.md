---
title: Upozornění kompilátoru (úroveň 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: b83b3b33727db300367156e10f902aaa6ff4bfdb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990769"
---
# <a name="compiler-warning-level-4-c4487"></a>Upozornění kompilátoru (úroveň 4) C4487

' derived_class_function ': shoduje se se zděděnou nevirtuální metodou ' base_class_function ', ale není explicitně označena jako ' New '

Funkce v odvozené třídě má stejný podpis jako nevirtuální funkce základní třídy. C4487 vás připomene, že funkce odvozené třídy nepřepisuje funkci základní třídy. Explicitně označte funkci odvozené třídy jako `new` pro vyřešení tohoto upozornění.

Další informace najdete v tématu [New (New slot v tabulce vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4487.

```cpp
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
