---
title: Upozornění kompilátoru (úroveň 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: d9aff4b554f4b162f87de9e1d373d59dea019637
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991742"
---
# <a name="compiler-warning-level-3-c4645"></a>Upozornění kompilátoru (úroveň 3) C4645

funkce deklarovaná pomocí __declspec (Return) obsahuje příkaz return.

Ve funkci, která je označená modifikátorem `__declspec` [return](../../cpp/noreturn.md) , byl nalezen [návratový](../../cpp/return-statement-in-program-termination-cpp.md) příkaz. Příkaz `return` byl ignorován.

Následující ukázka generuje C4645:

```cpp
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```
