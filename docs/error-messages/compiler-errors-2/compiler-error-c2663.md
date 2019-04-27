---
title: Chyba kompilátoru C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: d74326e49edd980896276e2c6e67526d8d769cb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360291"
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