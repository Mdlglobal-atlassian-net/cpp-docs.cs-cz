---
title: Compiler Error C2597
ms.date: 11/04/2016
f1_keywords:
- C2597
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
ms.openlocfilehash: b7bdd10ebd70eb61746690958532854dd98c6429
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228587"
---
# <a name="compiler-error-c2597"></a>Compiler Error C2597

Neplatný odkaz na Nestatický člen 'identifier'

Možné příčiny:

1. Nestatický člen určen ve statické členské funkce. Pro přístup k nestatickému členu, musíte předat nebo vytvořit místní instance třídy a operátor přístupu členů (`.` nebo `->`).

1. Zadaný identifikátor není členem třídy, struktury nebo sjednocení. Kontrola pravopisu identifikátor.

1. Operátor přístupu členů odkazuje na nečlenské funkce.

1. Následující ukázka generuje C2597 a ukazuje, jak ho opravit:

```
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