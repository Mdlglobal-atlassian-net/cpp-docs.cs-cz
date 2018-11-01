---
title: Chyba kompilátoru C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: d74326e49edd980896276e2c6e67526d8d769cb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644337"
---
# <a name="compiler-error-c2663"></a>Chyba kompilátoru C2663

'function': číslo přetížení mít žádné platné převody pro ukazatel "this"

Kompilátor nelze převést `this` k některé z přetížených verzí členskou funkci.

Tato chyba může být způsobena vyvoláním non -`const` členskou funkci na `const` objektu.  Možná řešení:

1. Odeberte `const` z deklarace objektu.

1. Přidat `const` do jednoho z přetížení funkce členů.

Následující ukázka generuje C2663:

```
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