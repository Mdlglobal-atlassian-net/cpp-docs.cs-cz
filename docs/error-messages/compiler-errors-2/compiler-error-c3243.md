---
title: Chyba kompilátoru C3243
ms.date: 11/04/2016
f1_keywords:
- C3243
helpviewer_keywords:
- C3243
ms.assetid: 35d8ad1a-377d-47df-be9d-c55eea23340f
ms.openlocfilehash: 280d7cf8ee79887cd188efb71eecfc8dbca08f3e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754560"
---
# <a name="compiler-error-c3243"></a>Chyba kompilátoru C3243

žádná z funkcí přetížení nebyla zavedena rozhraním Interface.

Pokusili jste se [explicitně přepsat](../../cpp/explicit-overrides-cpp.md) člena, který neexistuje v zadaném rozhraní.

Následující ukázka generuje C3243:

```cpp
// C3243.cpp
#pragma warning(disable:4199)
__interface IX14A {
   void g();
};

__interface IX14B {
   void f();
   void f(int);
};

class CX14 : public IX14A, public IX14B {
public:
   void IX14A::g();
   void IX14B::f();
   void IX14B::f(int);
};

void CX14::IX14A::f()   // C3243 occurs here
{
}
```
