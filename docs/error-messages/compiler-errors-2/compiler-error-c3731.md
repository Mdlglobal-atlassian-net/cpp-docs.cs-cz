---
title: Chyba kompilátoru C3731
ms.date: 11/04/2016
f1_keywords:
- C3731
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
ms.openlocfilehash: 9acf80eec0d36db64fa070d691533e7085754ac0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752948"
---
# <a name="compiler-error-c3731"></a>Chyba kompilátoru C3731

nekompatibilní událost ' Function1 ' a obslužná rutina ' function2 '; zdroj události a obslužná rutina události musí být stejného typu.

Zdroj události a přijímač událostí musí mít stejný typ (například `native` vs. `com` typy). Chcete-li tuto chybu opravit, zajistěte, aby byly typy zdroje událostí a obslužné rutiny události shodné.

Následující ukázka generuje C3731:

```cpp
// C3731.cpp
// compile with: /clr
#using <mscorlib.dll>
[event_source(native)]
struct A {
   __event void MyEvent();
};

[event_receiver(managed)]
// try the following line instead
// [event_receiver(native)]
struct B {
   void func();
   B(A a) {
      __hook(&A::MyEvent, &a, &B::func);   // C3731
   }
};

int main() {
}
```
