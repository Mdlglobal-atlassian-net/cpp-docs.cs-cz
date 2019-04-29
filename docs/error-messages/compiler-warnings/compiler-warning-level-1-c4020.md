---
title: Kompilátor upozornění (úroveň 1) C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: 75148c210ddd2a611061d58c036d12c084f442cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400043"
---
# <a name="compiler-warning-level-1-c4020"></a>Kompilátor upozornění (úroveň 1) C4020

'function': moc velký počet skutečných parametrů

Počet skutečných parametrů ve volání funkce překračuje počet formálních parametrů v prototypu funkce nebo definice. Kompilátor předá velmi skutečných parametrů podle konvence volání funkce.

Následující ukázka generuje C4020:

```
// C4020.c
// compile with: /W1 /c
void f(int);
int main() {
   f(1,2);   // C4020
}
```

Možná řešení:

```
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```