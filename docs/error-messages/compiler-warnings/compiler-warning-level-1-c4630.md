---
title: Kompilátor upozornění (úroveň 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 98ea72bef0cb95163604144c1069a13c3b27d81c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616252"
---
# <a name="compiler-warning-level-1-c4630"></a>Kompilátor upozornění (úroveň 1) C4630

'symbol': specifikátor třídy úložiště "extern" není platný pro definici členu

Datový člen nebo členskou funkci je definován jako `extern`. Členové nemohou být externím, i když můžete celé objekty. Kompilátor ignoruje `extern` – klíčové slovo. Následující ukázka generuje C4630:

```
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```