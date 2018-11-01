---
title: Chyba kompilátoru C3731
ms.date: 11/04/2016
f1_keywords:
- C3731
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
ms.openlocfilehash: 5acc33869648f83cd44bc557128c685f521ddf88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496054"
---
# <a name="compiler-error-c3731"></a>Chyba kompilátoru C3731

nekompatibilní událost "function1" a obslužnou rutinu 'function2'; Zdroj události a obslužné rutiny události musí být stejného typu

Zdroje událostí a příjemci událostí musí být stejného typu (například `native` vs. `com` typy). Chcete-li tuto chybu opravit, ujistěte se, typy zdroje událostí a shoda obslužné rutiny události.

Následující ukázka generuje C3731:

```
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