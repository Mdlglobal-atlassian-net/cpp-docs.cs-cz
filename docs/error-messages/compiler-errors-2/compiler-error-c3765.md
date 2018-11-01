---
title: C3765 chyby kompilátoru
ms.date: 11/04/2016
f1_keywords:
- C3765
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
ms.openlocfilehash: 86c043889c5342ed4f3edfc4d8a298bcbd345b3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456391"
---
# <a name="compiler-error-c3765"></a>C3765 chyby kompilátoru

'událost': nelze definovat událost ve třídě nebo struktuře "typ" označené jako event_receiver

Pokud má třída označení s [event_receiver](../../windows/event-receiver.md) atribut, nesmí obsahovat třídu [__event](../../cpp/event.md) deklarace.

Následující ukázka generuje C3765:

```
// C3765.cpp
[event_receiver(native)]
struct ER2 {
   __event void f();   // C3765
   __event void b(int);   // C3765
};
```