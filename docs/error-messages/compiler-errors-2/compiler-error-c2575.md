---
title: Chyba kompilátoru C2575
ms.date: 11/04/2016
f1_keywords:
- C2575
helpviewer_keywords:
- C2575
ms.assetid: 9eb45706-37ef-4481-b373-6d193ba13634
ms.openlocfilehash: a63696ba35a8b923f8fbf0c6d6387f2402969cff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755457"
---
# <a name="compiler-error-c2575"></a>Chyba kompilátoru C2575

identifikátor: jenom členské funkce a základy můžou být virtuální.

Globální funkce nebo třída je deklarována `virtual`. Toto není povoleno.

Následující ukázka generuje C2575:

```cpp
// C2575.cpp
// compile with: /c
virtual void func() {}   // C2575

void func2() {}
struct A {
   virtual void func2(){}
};
```
