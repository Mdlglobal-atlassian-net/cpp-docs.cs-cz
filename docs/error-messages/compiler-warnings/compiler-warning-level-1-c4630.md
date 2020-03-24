---
title: Upozornění kompilátoru (úroveň 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 414388fc1b9c6a7425d45e2ba92546960cadf404
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199612"
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
