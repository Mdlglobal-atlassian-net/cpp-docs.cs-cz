---
title: Upozornění kompilátoru (úroveň 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 893364183594782b825377f57fa4e525338d62d8
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052558"
---
# <a name="compiler-warning-level-1-c4630"></a>Upozornění kompilátoru (úroveň 1) C4630

' symbol ': specifikátor třídy úložiště ' extern ' není pro definici členu platný

Datový člen nebo členská funkce jsou definovány jako `extern`. Členové nemohou být externí, i když mohou být celé objekty. Kompilátor ignoruje klíčové slovo `extern`. Následující ukázka generuje C4630:

```cpp
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```