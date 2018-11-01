---
title: Kompilátor upozornění (úroveň 1) C4803
ms.date: 11/04/2016
f1_keywords:
- C4803
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
ms.openlocfilehash: 3915307ac2bcc6a923c93382cfefa618ce01fe52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563212"
---
# <a name="compiler-warning-level-1-c4803"></a>Kompilátor upozornění (úroveň 1) C4803

"metoda": metoda raise má jinou třídu úložiště než událost, "události.

Metody událostí musí mít stejnou třídu úložiště jako deklaraci události. Kompilátor upraví metody události tak, že třídy úložiště jsou stejné.

Toto upozornění může dojít, pokud máte třídu, která implementuje událost z rozhraní. Kompilátor negeneruje implicitně metodu vyvolat událost v rozhraní. Při implementaci tohoto rozhraní ve třídě, kompilátor implicitně generovat metodu raise a tato metoda nebude virtuální, proto upozornění. Další informace o událostech najdete v tématu [události](../../windows/event-cpp-component-extensions.md).

Zobrazit [upozornění](../../preprocessor/warning.md) direktivu pragma pro informace o tom, jak vypnout upozornění.

## <a name="example"></a>Příklad

Následující ukázka generuje C4803.

```
// C4803.cpp
// compile with: /clr /W1
using namespace System;

public delegate void Del();

ref struct E {
   Del ^ _pd1;
   event Del ^ E1 {
      void add (Del ^ pd1) {
         _pd1 = dynamic_cast<Del ^>(Delegate::Combine(_pd1, pd1));
      }

      void remove(Del^ pd1) {
         _pd1 = dynamic_cast<Del^> (Delegate::Remove(_pd1, pd1));
      }

      virtual void raise() {   // C4803 warning (remove virtual)
         if (_pd1)
            _pd1();
      }
   }

   void func() {
      Console::WriteLine("In E::func()");
   }
};

int main() {
   E ^ ep = gcnew E;
   ep->E1 += gcnew Del(ep, &E::func);
   ep->E1();
   ep->E1 -= gcnew Del(ep, &E::func);
   ep->E1();
}
```
