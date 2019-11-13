---
title: Upozornění kompilátoru (úroveň 1) C4927
ms.date: 11/04/2016
f1_keywords:
- C4927
helpviewer_keywords:
- C4927
ms.assetid: 7009e740-a2ef-4130-96ba-482e092f717a
ms.openlocfilehash: 8e56d185f6f87bc6e381ccec9ed8bd50ba3e2245
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052287"
---
# <a name="compiler-warning-level-1-c4927"></a>Upozornění kompilátoru (úroveň 1) C4927

Neplatný převod; implicitně se používá víc než jeden uživatelsky definovaný převod.

Více než jeden uživatelsky definovaný převod je implicitně aplikovaný na jednu hodnotu – kompilátor nenalezl explicitní převod, ale našel převod, který se použil.

Následující ukázka generuje C4927:

```cpp
// C4927.cpp
// compile with: /W1
struct B
{
   operator int ()
   {
      return 0;
   }
};

struct A
{
   A(int i)
   {
   }

   /*
   // uncomment this constructor to resolve
   A(B b)
   {
   }
   */
};

A f1( B& b)
{
   return A(b);
}

B& f2( B& b)
{
   return b;
}

A f()
{
   B b;
   return A(b);   // ok
   return f1(b);  // ok
   return b;      // C4927
   return B(b);   // C4927
   return f2(b);  // C4927
}

int main()
{
   B b;
   A a = b;
   A a2(b);
}
```