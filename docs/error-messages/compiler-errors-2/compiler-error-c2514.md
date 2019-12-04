---
title: Chyba kompilátoru C2514
ms.date: 11/04/2016
f1_keywords:
- C2514
helpviewer_keywords:
- C2514
ms.assetid: 4b7085e5-6714-4261-80b7-bc72e64ab3e8
ms.openlocfilehash: e0153ec9d48225d153221f2192761da4023fab96
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746510"
---
# <a name="compiler-error-c2514"></a>Chyba kompilátoru C2514

Class: třída nemá žádné konstruktory.

Třída, struktura nebo sjednocení nemá žádný konstruktor se seznamem parametrů, který by odpovídal parametrům, které se používají k vytvoření instance.

Třída musí být plně deklarována před tím, než může být vytvořena instance.

Následující ukázka generuje C2514:

```cpp
// C2514.cpp
// compile with: /c
class f;

class g {
public:
    g (int x);
};

class fmaker {
   f *func1() {
      return new f(2);   // C2514
   }

   g *func2() {
      return new g(2);   // OK
   }
};
```
