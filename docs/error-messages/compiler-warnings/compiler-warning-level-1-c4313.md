---
title: Kompilátor upozornění (úroveň 1) C4313
ms.date: 11/04/2016
f1_keywords:
- C4313
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
ms.openlocfilehash: 774af2d5d29112d56adf97e22d1bdd758a816ef1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555702"
---
# <a name="compiler-warning-level-1-c4313"></a>Kompilátor upozornění (úroveň 1) C4313

'function': 'specifikátor formátu"ve formátu řetězce je v konfliktu s číslo argumentu typu 'type'

Dojde ke konfliktu mezi zadaný formát a hodnotu, která předáváte. Například předán parametr 64-bit neúplný %d specifikátoru formátu, který očekává parametr 32bitové celé číslo. Toto upozornění je platná pouze při kompilaci kódu pro 64bitové cíle.

## <a name="example"></a>Příklad

Následující ukázka kódu generuje C4313 při kompilaci pro 64bitové cílové.

```
// C4313.cpp
// Compile by using: cl /W1 C4313.cpp
#include <stdio.h>
int main() {
   int * pI = 0;
   printf("%d", pI);   // C4313 on 64-bit platform code
   // Try one of the following lines instead:
   // printf("%p\n", pI);
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information
}
```