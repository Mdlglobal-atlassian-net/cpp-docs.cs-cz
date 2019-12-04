---
title: Chyba kompilátoru C2254
ms.date: 11/04/2016
f1_keywords:
- C2254
helpviewer_keywords:
- C2254
ms.assetid: 49bb3d7e-3bdf-4af6-937c-fa627be412a9
ms.openlocfilehash: 38220575a48720a9df0e232ef74c8743e7e056c7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758837"
---
# <a name="compiler-error-c2254"></a>Chyba kompilátoru C2254

' function ': specifikátor Pure nebo abstract override není povolený pro funkci Friend.

Funkce `friend` je určena jako Pure `virtual`.

Následující ukázka generuje C2254:

```cpp
// C2254.cpp
// compile with: /c
class A {
public:
   friend void func1() = 0;   // C2254, func1 is friend
   void virtual func2() = 0;   // OK, pure virtual
   friend void func3();   // OK, friend not virtual nor pure
};

void func1() {};
void func3() {};
```
