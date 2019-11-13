---
title: Upozornění kompilátoru (úroveň 1) C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: f54f29fcbc6fb71033bc6d1d87c7ddb31622ee40
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051259"
---
# <a name="compiler-warning-level-1-c4822"></a>Upozornění kompilátoru (úroveň 1) C4822

' member ': členská funkce lokální třídy nemá tělo

Členská funkce lokální třídy je deklarovaná, ale není definovaná ve třídě. Chcete-li použít členskou funkci lokální třídy, je nutné ji definovat ve třídě. Nelze jej deklarovat ve třídě a definovat jej mimo třídu.

Jakákoli definice mimo třídu členské funkce lokální třídy bude chyba.

Následující ukázka generuje C4822:

```cpp
// C4822.cpp
// compile with: /W1
int main() {
   struct C {
      void func1(int);   // C4822
      // try the following line instead
      // void func1(int){}
  };
}
```