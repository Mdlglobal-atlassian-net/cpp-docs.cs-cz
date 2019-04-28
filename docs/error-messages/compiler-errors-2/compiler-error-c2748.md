---
title: Chyba kompilátoru C2748
ms.date: 11/04/2016
f1_keywords:
- C2748
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
ms.openlocfilehash: 251492b736ba3325ed263a9a8754fc8fa480c664
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360226"
---
# <a name="compiler-error-c2748"></a>Chyba kompilátoru C2748

spravované nebo vytvoření pole WinRT musí mít velikost pole nebo inicializátor pole.

Spravovat A nebo pole WinRT byl chybně vytvořen. Další informace najdete v tématu [pole](../../extensions/arrays-cpp-component-extensions.md).

Následující ukázka generuje C2748 a ukazuje, jak ho opravit:

```
// C2748.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>();   // C2748
   // try the following line instead
   array<int> ^p2 = new array<int>(2);
}
```