---
title: Chyba kompilátoru C2452
ms.date: 11/04/2016
f1_keywords:
- C2452
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
ms.openlocfilehash: 3e2d583efa2b634cf49d8588fa398bd81f24c607
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208756"
---
# <a name="compiler-error-c2452"></a>Chyba kompilátoru C2452

'type': Neplatný zdrojový typ pro přetypování safe_cast

Zdrojový typ pro [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) nebyla platná.  Například všechny typy v `safe_cast` operace musí být typy CLR.

Následující ukázka generuje C2452:

```
// C2452.cpp
// compile with: /clr

struct A {};
struct B : public A {};

ref struct C {};
ref struct D : public C{};

int main() {
   A a;
   safe_cast<B*>(&a);   // C2452

   // OK
   C ^ c = gcnew C;
   safe_cast<D^>(c);
}
```