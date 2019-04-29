---
title: Kompilátor upozornění (úroveň 1) C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: 02e7ba11f7bda134bcc98ce2c494a3ef367c0d6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378502"
---
# <a name="compiler-warning-level-1-c4822"></a>Kompilátor upozornění (úroveň 1) C4822

'member': členská funkce lokální třídy nemá tělo.

Členská funkce lokální třídy byla deklarována, ale není definovaný ve třídě. Pokud chcete použít členská funkce lokální třídy, musí být definovat ve třídě. Nelze deklarovat v třídě a definování mimo třídy.

Všechny definice mimo třídu pro členská funkce lokální třídy bude k chybě.

Následující ukázka generuje C4822:

```
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