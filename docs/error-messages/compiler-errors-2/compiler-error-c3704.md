---
title: Chyba kompilátoru C3704
ms.date: 11/04/2016
f1_keywords:
- C3704
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
ms.openlocfilehash: 4e26742de6c294018f81c6f49c1719fdb11d5149
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467103"
---
# <a name="compiler-error-c3704"></a>Chyba kompilátoru C3704

'function': metoda vararg nemůže aktivovat události

Pokusili jste se použít [__event](../../cpp/event.md) na metoda vararg. Chcete-li tuto chybu opravit, nahraďte `fireEvent(int i, ...)` volání s `fireEvent(int i)` volání, jak je znázorněno v následujícím příkladu kódu.

Následující ukázka generuje C3704:

```
// C3704.cpp
[ event_source(native) ]
class CEventSrc {
   public:
      __event void fireEvent(int i, ...);   // C3704
      // try the following line instead:
      // __event void fireEvent(int i);
};

int main() {
}
```