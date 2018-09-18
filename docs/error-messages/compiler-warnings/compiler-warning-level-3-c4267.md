---
title: Upozornění (úroveň 3) C4267 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4267
dev_langs:
- C++
helpviewer_keywords:
- C4267
ms.assetid: 2fa2f13f-fa4f-47bb-ad8f-6cb19cfc91e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 359b254c937eb0c52edd56ae9a2616bfea764213
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097037"
---
# <a name="compiler-warning-level-3-c4267"></a>Kompilátor upozornění (úroveň 3) C4267

'příkaz var': převod z parametr size_t' na typ, může dojít ke ztrátě dat.

Kompilátor zjistil konverzi `size_t` na menší typ.

Chcete-li opravit toto upozornění, použijte `size_t` místo `type`. Můžete také použít celočíselného typu, který je přinejmenším stejně velká jako `size_t`.

## <a name="example"></a>Příklad

Následující příklad generuje C4267.

```
// C4267.cpp
// compile by using: cl /W4 C4267.cpp
void Func1(short) {}
void Func2(int) {}
void Func3(long) {}
void Func4(size_t) {}

int main() {
   size_t bufferSize = 10;
   Func1(bufferSize);   // C4267 for all platforms
   Func2(bufferSize);   // C4267 only for 64-bit platforms
   Func3(bufferSize);   // C4267 only for 64-bit platforms
   Func4(bufferSize);   // OK for all platforms
}
```