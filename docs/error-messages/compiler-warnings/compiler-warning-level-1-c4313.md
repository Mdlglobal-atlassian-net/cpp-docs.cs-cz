---
title: Upozornění kompilátoru (úroveň 1) C4313
ms.date: 11/04/2016
f1_keywords:
- C4313
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
ms.openlocfilehash: 14ac938d62b4c5b6f22957268721aea9c3ffef22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163047"
---
# <a name="compiler-warning-level-1-c4313"></a>Upozornění kompilátoru (úroveň 1) C4313

' function ': ' specifikátor formátu ' ve formátovacím řetězci je v konfliktu s argumentem typu ' type '

Došlo ke konfliktu mezi zadaným formátem a hodnotou, kterou předáváte. Například jste předali 64 parametr bitu nekvalifikovanému specifikátoru formátu% d, který očekává parametr 32-bit integer. Toto upozornění je platné pouze v případě, že je kód kompilován pro 64 cíle.

## <a name="example"></a>Příklad

Následující ukázka kódu generuje C4313 při kompilování pro 64 cíl.

```cpp
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
