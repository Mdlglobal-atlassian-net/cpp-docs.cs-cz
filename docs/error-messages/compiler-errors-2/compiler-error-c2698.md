---
title: Chyba kompilátoru C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: 6129ff691f804b31fdb8cb487ac4609e4bca6ef2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755184"
---
# <a name="compiler-error-c2698"></a>Chyba kompilátoru C2698

deklarace using-Declaration pro deklaraci 1 nemůže současně existovat společně s existující deklarací using-Declaration pro deklaraci 2.

Po [použití deklarace](../../cpp/using-declaration.md) pro datový člen není povolena deklarace using ve stejném oboru, který používá stejný název, protože pouze funkce mohou být přetíženy.

Následující ukázka generuje C2698:

```cpp
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```
