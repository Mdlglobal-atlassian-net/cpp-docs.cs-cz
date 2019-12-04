---
title: Chyba kompilátoru C3765
ms.date: 11/04/2016
f1_keywords:
- C3765
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
ms.openlocfilehash: 8a12bdfaf0931fb0a94dafc289f9ae39aef61f23
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757229"
---
# <a name="compiler-error-c3765"></a>Chyba kompilátoru C3765

' Event ': nelze definovat událost ve třídě/struktuře ' type ' označenou jako event_receiver

Pokud je třída označena atributem [event_receiver](../../windows/event-receiver.md) , třída nemůže obsahovat deklaraci [__event](../../cpp/event.md) .

Následující ukázka generuje C3765:

```cpp
// C3765.cpp
[event_receiver(native)]
struct ER2 {
   __event void f();   // C3765
   __event void b(int);   // C3765
};
```
