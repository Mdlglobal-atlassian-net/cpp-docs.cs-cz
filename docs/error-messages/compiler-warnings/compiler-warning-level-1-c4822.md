---
title: Upozornění kompilátoru (úroveň 1) C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: 59c42227c7e8be9bd31c37776d9724d23db61837
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174866"
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
