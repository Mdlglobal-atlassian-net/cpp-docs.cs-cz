---
title: Chyba kompilátoru C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: f643b7d8c035b4d1d7d8806feb5b121cf76d7796
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651904"
---
# <a name="compiler-error-c2698"></a>Chyba kompilátoru C2698

deklarace using pro ' Deklarace 1 nemůže koexistovat s existující deklarace using pro ' deklarace 2

Jakmile budete mít [using – deklarace](../../cpp/using-declaration.md) pro datového člena, jakékoli pomocí deklarace ve stejném oboru, který používá stejný název není povolená, protože mohou být přetíženy pouze funkce.

Následující ukázka generuje C2698:

```
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