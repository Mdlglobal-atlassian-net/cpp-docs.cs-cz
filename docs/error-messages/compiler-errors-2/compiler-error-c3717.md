---
title: Chyba kompilátoru C3717
ms.date: 11/04/2016
f1_keywords:
- C3717
helpviewer_keywords:
- C3717
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
ms.openlocfilehash: cd9a97f1b0d9c9eecfa6a42f735f21a42fd846e9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753234"
---
# <a name="compiler-error-c3717"></a>Chyba kompilátoru C3717

' Method ': nejde definovat metodu, která aktivuje události.

Deklarovali jste metodu události, která zahrnuje implementaci. Deklarace metody [__event](../../cpp/event.md) nemůže mít definici. Chcete-li tuto chybu opravit, zajistěte, aby žádné deklarace metod události neměly definice. Například v následujícím kódu odstraňte tělo funkce z deklarace `event1`, jak je uvedeno v komentářích.

Následující ukázka generuje C3717:

```cpp
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
