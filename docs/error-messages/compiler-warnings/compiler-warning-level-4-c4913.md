---
title: Kompilátor upozornění (úroveň 4) C4913
ms.date: 11/04/2016
f1_keywords:
- C4913
helpviewer_keywords:
- C4913
ms.assetid: b94aa52e-6029-4170-9134-017714931546
ms.openlocfilehash: a06fda0999e5f164fca81917cecbb63312fea25d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359979"
---
# <a name="compiler-warning-level-4-c4913"></a>Kompilátor upozornění (úroveň 4) C4913

**uživatel definovaný binární operátor ',' existuje, ale přetížení nemohlo převést všechny operandy, předdefinovaný binární operátor ',' používá**

V programu v jazyce, který také měl operátor přetížené čárkou; došlo k volání operátor čárky integrované převod, který jste přiměje mohlo dojít ne.

Následující ukázka kódu generuje C4913:

```
// C4913.cpp
// compile with: /W4
struct A
{
};

struct S
{
};

struct B
{
   // B() { }
   // B(S &s) { s; }
};

B operator , (A a, B b)
{
   a;
   return b;
}

int main()
{
   A a;
   B b;
   S s;

   a, b;   // OK calls user defined operator
   a, s;   // C4913 uses builtin comma operator
           // uncomment the conversion code in B to resolve.
}
```