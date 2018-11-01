---
title: Kompilátor upozornění (úroveň 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: a3e5c834a3f14b9a125176dcddd5bcc355cf1faa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536770"
---
# <a name="compiler-warning-level-3-c4645"></a>Kompilátor upozornění (úroveň 3) C4645

funkce deklarovaná pomocí __declspec(noreturn) má návratový příkaz

A [vrátit](../../cpp/return-statement-in-program-termination-cpp.md) příkaz nebyl nalezen ve funkci, která je označena [noreturn](../../cpp/noreturn.md) `__declspec` modifikátor. `return` Příkazu byl ignorován.

Následující ukázka generuje C4645:

```
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```