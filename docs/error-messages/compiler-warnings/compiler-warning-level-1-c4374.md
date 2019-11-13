---
title: Upozornění kompilátoru (úroveň 1) C4374
ms.date: 11/04/2016
f1_keywords:
- C4374
helpviewer_keywords:
- C4374
ms.assetid: 4ac9aaec-d815-4b6e-825f-fa872092dd3b
ms.openlocfilehash: 31a43467020e3d90a2f02c667f7cdb6177b4d833
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966443"
---
# <a name="compiler-warning-level-1-c4374"></a>Upozornění kompilátoru (úroveň 1) C4374

' Function1 ': metoda rozhraní nebude implementována jinou nevirtuální metodou ' function2 '

Kompilátor očekával najít klíčové slovo [Virtual](../../cpp/virtual-specifier.md) v definici metody.

Následující ukázka generuje C4374:

```cpp
// C4374.cpp
// compile with: /clr /W1 /c /WX
public interface class I {
   void f();
};

public ref struct B {
   void f() {
      System::Console::WriteLine("B::f()");
   }
};

public ref struct C {
   virtual void f() {
      System::Console::WriteLine("C::f()");
   }
};

public ref struct D : B, I {};   // C4374
public ref struct E : C, I {};   // OK
```