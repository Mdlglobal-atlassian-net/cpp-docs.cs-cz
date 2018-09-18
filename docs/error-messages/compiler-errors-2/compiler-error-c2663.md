---
title: Chyba kompilátoru C2663 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2663
dev_langs:
- C++
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fed35dcce056eb3d2a660c154e94b8058563dba7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083688"
---
# <a name="compiler-error-c2663"></a>Chyba kompilátoru C2663

'function': číslo přetížení mít žádné platné převody pro ukazatel "this"

Kompilátor nelze převést `this` k některé z přetížených verzí členskou funkci.

Tato chyba může být způsobena vyvoláním non -`const` členskou funkci na `const` objektu.  Možná řešení:

1. Odeberte `const` z deklarace objektu.

1. Přidat `const` do jednoho z přetížení funkce členů.

Následující ukázka generuje C2663:

```
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```