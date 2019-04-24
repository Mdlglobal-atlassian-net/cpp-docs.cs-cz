---
title: Chyba kompilátoru C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 9bfdf8b26ab599ef1a28483af7ebc28f0dbc1912
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328338"
---
# <a name="compiler-error-c3714"></a>Chyba kompilátoru C3714

"metoda": metoda obslužné rutiny události musí mít stejnou volací konvenci jako zdroj "metodu.

Definujete metodu obslužné rutiny události, která nepoužívá stejnou volací konvenci jako zdroj událostí metodu. Chcete-li vyřešit tuto chybu, poskytněte metodu obslužné rutiny události stejné konvence volání jako metodu zdroje události. Například v následujícím kódu je konvence volání z `handler1` a `event1` odpovídají ([__cdecl](../../cpp/cdecl.md) nebo [__stdcall](../../cpp/stdcall.md) nebo jinými). Odebrání klíčová slova konvence volání z obou deklarace se také problém vyřešit a způsobit, že `event1` a `handler1` na výchozím nastavení [thiscall](../../cpp/thiscall.md) konvence volání. Zobrazit [konvence volání](../../cpp/calling-conventions.md) Další informace.

Následující ukázka generuje C3714:

```
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