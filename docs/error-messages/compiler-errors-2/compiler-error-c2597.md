---
title: Chyba kompilátoru C2597
ms.date: 11/04/2016
f1_keywords:
- C2597
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
ms.openlocfilehash: 680268948f8642b02768bd4b3092666982e14eb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759305"
---
# <a name="compiler-error-c2597"></a>Chyba kompilátoru C2597

Neplatný odkaz na identifikátor nestatického členu

Možné příčiny:

1. Ve statické členské funkci je určen nestatický člen. Chcete-li získat přístup k nestatickému členu, musíte předat nebo vytvořit místní instanci třídy a použít operátor přístupu členů (`.` nebo `->`).

1. Zadaný identifikátor není členem třídy, struktury nebo sjednocení. Zkontrolujte pravopis identifikátoru.

1. Operátor přístupu členů odkazuje na nečlenskou funkci.

1. Následující ukázka generuje C2597 a ukazuje, jak ji opravit:

```cpp
// C2597.cpp
// compile with: /c
struct s1 {
   static void func();
   static void func2(s1&);
   int i;
};

void s1::func() {
   i = 1;    // C2597 - static function can't access non-static data member
}

// OK - fix by passing an instance of s1
void s1::func2(s1& a) {
   a.i = 1;
}
```
