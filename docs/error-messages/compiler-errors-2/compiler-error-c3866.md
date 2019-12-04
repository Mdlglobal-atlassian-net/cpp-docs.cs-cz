---
title: Chyba kompilátoru C3866
ms.date: 11/04/2016
f1_keywords:
- C3866
helpviewer_keywords:
- C3866
ms.assetid: 685870af-2440-4cdf-a6cb-284a5b96ef9d
ms.openlocfilehash: 907e435b31a825021b03946f08f7307c5e1ed708
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761454"
---
# <a name="compiler-error-c3866"></a>Chyba kompilátoru C3866

v volání funkce chybí seznam argumentů.

Uvnitř nestatické členské funkce neměl volání destruktoru nebo finalizační metody seznam argumentů.

Následující ukázka generuje C3866:

```cpp
// C3866.cpp
// compile with: /c
class C {
   ~C();
   void f() {
      this->~C;   // C3866
      this->~C();   // OK
   }
};
```
