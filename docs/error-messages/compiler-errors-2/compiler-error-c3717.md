---
title: Chyba kompilátoru C3717
ms.date: 11/04/2016
f1_keywords:
- C3717
helpviewer_keywords:
- C3717
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
ms.openlocfilehash: f7e60b4f1b6a1337ef93088e4f36ce2a1b34dc47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599301"
---
# <a name="compiler-error-c3717"></a>Chyba kompilátoru C3717

'metody': nelze definovat metodu, která aktivuje události

Můžete deklarovat metodu události, která zahrnuje implementace. [__Event](../../cpp/event.md) deklarace metody nemůže mít definici. Chcete-li vyřešit tuto chybu, zajistěte, aby definice deklarace metody žádné události. Například v následujícím kódu odebrat tělo funkce z `event1` deklaraci je uvedené poznámky.

Následující ukázka generuje C3717:

```
// C3717.cpp
[event_source(native)]
class CEventSrc {
public:
   __event void event1() {   // C3717
   }

   // remove definition for event1 and substitute following declaration
   // __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {
   }

   void HookEvents(CEventSrc* pSrc) {
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};

int main() {
}
```