---
title: Chyba kompilátoru C3743
ms.date: 11/04/2016
f1_keywords:
- C3743
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
ms.openlocfilehash: 137913e0c6909712cbb6745666112d315925ab0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618995"
---
# <a name="compiler-error-c3743"></a>Chyba kompilátoru C3743

můžete pouze hook/vyjmutí celé rozhraní při "má" parametr třídy event_receiver hodnotu true

[__Unhook](../../cpp/unhook.md) funkce se liší v počtu parametrů, které trvá založené na hodnotu předanou `layout_dependent` parametr [event_receiver](../../windows/event-receiver.md) třídy.

Následující ukázka generuje C3743:

```
// C3743.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];
[object] __interface I { HRESULT f(); };

[event_receiver(com, layout_dependent=true), coclass]
struct R : I {
        HRESULT f() {
      return 0;
   }
        R() {
   }

   R(I* a) {
      __hook(I, a, &R::f);   // C3743
      // The following line resolves the error.
      // __hook(I, a);
   }
};
```