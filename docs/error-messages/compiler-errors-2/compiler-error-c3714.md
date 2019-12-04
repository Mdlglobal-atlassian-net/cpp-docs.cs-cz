---
title: Chyba kompilátoru C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 1078bf8a97f6cb7afeaf7046489fe262c0bb0199
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753325"
---
# <a name="compiler-error-c3714"></a>Chyba kompilátoru C3714

' Method ': metoda obslužné rutiny události musí mít stejnou konvenci volání jako zdroj ' Method ' '

Definovali jste metodu obslužné rutiny události, která nepoužívala stejnou konvenci volání jako zdrojová metoda události. Chcete-li tuto chybu opravit, poskytněte metodu obslužné rutiny události stejné konvence volání jako metody zdrojové události. Například v následujícím kódu proveďte konvence volání `handler1` a `event1` ([__cdecl](../../cpp/cdecl.md) nebo [__stdcall](../../cpp/stdcall.md) nebo jiné). Odebrání klíčových slov konvence volání z obou deklarací také vyřeší problém a způsobí, že `event1` a `handler1` výchozí konvenci volání [thiscall](../../cpp/thiscall.md) . Další informace najdete v tématu věnovaném [konvencím volání](../../cpp/calling-conventions.md) .

Následující ukázka generuje C3714:

```cpp
// C3714.cpp
// compile with: /c
// processor: x86
[event_source(native)]
class CEventSrc {
public:
   __event void __cdecl event1();
   // try the following line instead
   // __event void __stdcall event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void __stdcall handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3714
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3714
   }
};
```
