---
title: Upozornění (úroveň 3) C4645 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4645
dev_langs:
- C++
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b597678e726d6b10240c442ed7e48698a993e2fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046534"
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