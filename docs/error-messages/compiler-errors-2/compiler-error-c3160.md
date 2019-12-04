---
title: Chyba kompilátoru C3160
ms.date: 11/04/2016
f1_keywords:
- C3160
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
ms.openlocfilehash: 4d6f415c8b3c8275ac45ef4d4313021100d9a833
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755145"
---
# <a name="compiler-error-c3160"></a>Chyba kompilátoru C3160

' pointer ': datový člen spravované nebo třídy WinRT nemůže mít tento typ

Vnitřní ukazatele pro uvolňování paměti mohou ukazovat na vnitřek spravované nebo třídy WinRT. Protože jsou pomalejší než ukazatele na celé objekty a vyžadují speciální zpracování systémem uvolňování paměti, nelze deklarovat vnitřně spravované ukazatele jako členy třídy.

Následující ukázka generuje C3160:

```cpp
// C3160.cpp
// compile with: /clr
ref struct A {
   // cannot create interior pointers inside a class
   interior_ptr<int> pg;   // C3160
   int g;   // OK
   int* pg2;   // OK
};

int main() {
   interior_ptr<int> pg2;   // OK
}
```
