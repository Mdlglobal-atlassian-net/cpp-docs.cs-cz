---
title: Kompilátor upozornění (úroveň 3) C4267
ms.date: 11/04/2016
f1_keywords:
- C4267
helpviewer_keywords:
- C4267
ms.assetid: 2fa2f13f-fa4f-47bb-ad8f-6cb19cfc91e6
ms.openlocfilehash: 31e5b9a9b8e7b25a0d54648ce808ff6266a27321
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402174"
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