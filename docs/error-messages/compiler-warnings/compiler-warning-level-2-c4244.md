---
title: Kompilátor upozornění (úroveň 2) C4244
ms.date: 11/04/2016
f1_keywords:
- C4244
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
ms.openlocfilehash: af821d80ff8c4c7717986f2ff4d0f3392cd6fca3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523090"
---
# <a name="compiler-warning-level-2-c4244"></a>Kompilátor upozornění (úroveň 2) C4244

'argument': převod z 'type1' na 'type2', možná ztráta dat

A s plovoucí desetinnou čárkou typu bodu byl převeden na typ integer.  Může dojít ke ztrátě dat, mohlo dojít.

Pokud se zobrazí C4244, si změnit program používat typy kompatibilní, nebo přidat nějaké logiky do kódu, aby se zajistilo, že rozsah možných hodnot bude vždy kompatibilní s typy, které používáte.

Na úrovni 3 a 4; můžete také vyvolat C4244 Zobrazit [upozornění kompilátoru (úrovně 3 a 4) C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C4244:

```
// C4244_level2.cpp
// compile with: /W2

int f(int x){ return 0; }
int main() {
   double x = 10.1;
   int i = 10;
   return (f(x));   // C4244
   // try the following line instead
   // return (f(i));
}
```