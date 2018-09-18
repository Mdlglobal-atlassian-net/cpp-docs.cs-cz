---
title: Chyba kompilátoru C2597 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2597
dev_langs:
- C++
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9f8deb325ae54393518698263f3ca93ca88ca48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114446"
---
# <a name="compiler-error-c2597"></a>Chyba kompilátoru C2597

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