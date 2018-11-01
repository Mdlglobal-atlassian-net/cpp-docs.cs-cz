---
title: Kompilátor upozornění (úroveň 4) C4610
ms.date: 11/04/2016
f1_keywords:
- C4610
helpviewer_keywords:
- C4610
ms.assetid: 23c1a16c-9ca9-4bf6-9911-a72b785560c2
ms.openlocfilehash: ce671552083f4e6b055c52e7387d3a95e7d47c0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559988"
---
# <a name="compiler-warning-level-4-c4610"></a>Kompilátor upozornění (úroveň 4) C4610

objekt 'class' možné nikdy instancovat - vyžaduje konstruktor definovaný uživatelem.

Třída nemá žádné uživatelem definované nebo výchozí konstruktory. Je provedena bez vytvoření instance. Následující ukázka generuje C4610:

```
// C4610.cpp
// compile with: /W4
struct A {
   int &j;

   A& A::operator=( const A& );
};   // C4610

/* use this structure definition to resolve the warning
struct B {
   int &k;

   B(int i = 0) : k(i) {
   }

   B& B::operator=( const B& );
} b;
*/

int main() {
}
```