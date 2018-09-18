---
title: Chyba kompilátoru C3714 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3714
dev_langs:
- C++
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7102378acc2fe12335f1f2b3579f93cf02161b16
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109649"
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