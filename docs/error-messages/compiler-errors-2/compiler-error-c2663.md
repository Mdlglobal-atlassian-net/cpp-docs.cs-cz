---
title: Chyba kompilátoru C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f07b63202d8f171dfb69f4bb294b392152b9290b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756029"
---
# <a name="compiler-error-c2663"></a>Chyba kompilátoru C2663

' function ': počet přetížení nemá žádné právní převody pro ukazatel ' this '

Kompilátor nemohl převést `this` na žádné přetížené verze členské funkce.

Tato chyba může být způsobena voláním členské funkce, která není`const`, na objektu `const`.  Možná řešení:

1. Odeberte `const` z deklarace objektu.

1. Přidejte `const` k jednomu z převedených členských funkcí.

Následující ukázka generuje C2663:

```cpp
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```
