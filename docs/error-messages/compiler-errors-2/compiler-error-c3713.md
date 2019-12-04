---
title: Chyba kompilátoru C3713
ms.date: 11/04/2016
f1_keywords:
- C3713
helpviewer_keywords:
- C3713
ms.assetid: 75c6b9b6-955b-49bd-9bc8-ced88b496a1f
ms.openlocfilehash: d78d1fb3028e8618035c1c6f7bb3eb0f65409dd2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753351"
---
# <a name="compiler-error-c3713"></a>Chyba kompilátoru C3713

' Method ': metoda obslužné rutiny události musí mít stejné parametry funkce jako zdroj ' Method ' '

Definovali jste metodu obslužné rutiny události, která nepoužívala stejné parametry jako zdrojová metoda události. Chcete-li tuto chybu opravit, poskytněte obslužné rutině události stejné parametry jako metody zdrojové události.

Následující ukázka generuje C3713:

```cpp
// C3713.cpp
// compile with: /c
[event_source(native)]
class CEventSrc {
public:
   __event void event1(int nValue);
   // try the following line instead
   // __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3713
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3713
   }
};
```
