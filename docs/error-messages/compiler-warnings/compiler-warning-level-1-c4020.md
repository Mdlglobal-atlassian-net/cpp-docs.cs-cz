---
title: Upozornění kompilátoru (úroveň 1) C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: ccab8eaac42932491fc8b88cd28f2d3334b2e849
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626325"
---
# <a name="compiler-warning-level-1-c4020"></a>Upozornění kompilátoru (úroveň 1) C4020

' function ': moc velký počet skutečných parametrů

Počet skutečných parametrů ve volání funkce překračuje počet formálních parametrů v prototypu nebo definici funkce. Kompilátor předá další skutečné parametry podle konvence volání funkce.

Následující ukázka generuje C4020:

```c
// C4020.c
// compile with: /W1 /c
void f(int);
int main() {
   f(1,2);   // C4020
}
```

Možné řešení:

```c
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```