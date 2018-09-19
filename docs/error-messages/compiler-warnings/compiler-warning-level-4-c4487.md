---
title: Upozornění (úroveň 4) C4487 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4487
dev_langs:
- C++
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffc1a25d362cad95f2aad43d626e4918955903f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135838"
---
# <a name="compiler-warning-level-4-c4487"></a>Kompilátor upozornění (úroveň 4) C4487

'derived_class_function': odpovídá zděděnou nevirtuální metodu "base_class_function", ale není explicitně označené jako new.

Funkce v odvozené třídě nemá stejný podpis jako funkci nevirtuální základní třídy. C4487 upozorňuje, že odvozené třídy funkce nemůže přepsat funkci základní třídy. Explicitně označit funkce odvozené třídy jako `new` vyřešit tato upozornění.

Další informace najdete v tématu [new (nový slot v tabulce vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md).

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