---
title: Chyba kompilátoru C3731 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3731
dev_langs:
- C++
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 526cd57bd18d379f7c85bbe98bc7fb2dc37b9c41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099909"
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