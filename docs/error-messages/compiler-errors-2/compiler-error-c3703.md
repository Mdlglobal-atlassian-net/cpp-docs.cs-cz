---
title: Chyba kompilátoru C3703
ms.date: 11/04/2016
f1_keywords:
- C3703
helpviewer_keywords:
- C3703
ms.assetid: 7e3677d9-f2be-4c26-998f-423564e9023c
ms.openlocfilehash: 0b34760bc3f5b23148ce84cf590685efad2008df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324633"
---
# <a name="compiler-error-c3703"></a>Chyba kompilátoru C3703

obslužné rutiny události: metoda obslužné rutiny události musí mít stejnou třídu úložiště jako zdroj "události.

[Události](../../cpp/event-handling.md) má jinou třídu úložiště než obslužná rutina události, ke kterému je připojeno. Například tato chyba nastane, pokud obslužná rutina události je statickou členskou funkcí a události není statická. Chcete-li tuto chybu opravit, dejte události a obslužné rutiny události stejnou třídu úložiště.

Následující ukázka generuje C3703:

```
// C3703.cpp
// C3703 expected
#include <stdio.h>

[event_source(type=native)]
class CEventSrc {
public:
   __event static void MyEvent();
};

[event_receiver(type=native)]
class CEventHandler {
public:
   // delete the following line to resolve
   void MyHandler() {}

   // try the following line instead
   // static void MyHandler() {}

   void HookIt(CEventSrc* pSource) {
      __hook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }

   void UnhookIt(CEventSrc* pSource) {
      __unhook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }
};

int main() {
   CEventSrc src;
   CEventHandler hnd;

   hnd.HookIt(&src);
   __raise src.MyEvent();
   hnd.UnhookIt(&src);
}
```