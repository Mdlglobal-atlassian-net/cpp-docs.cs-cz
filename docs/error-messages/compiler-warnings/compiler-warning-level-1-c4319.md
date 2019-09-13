---
title: Upozornění kompilátoru (úroveň 1) C4319
ms.date: 01/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: 2d5ae8fcf5a527031c3a974b227f713675f31ffa
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926105"
---
# <a name="compiler-warning-level-1-c4319"></a>Upozornění kompilátoru (úroveň 1) C4319

> ~: nulová hodnota "*typ1*" na "*typ2*" o větší velikost

Výsledek operátoru **~** (bitového doplňku) je nepodepsaný a pak se při převodu na větší typ rozšíří nulou.

## <a name="example"></a>Příklad

V následujícím příkladu `~(a - 1)` je vyhodnocen jako 32 řetězec s nepodepsaným znaménkem a poté převeden na 64 bitů pomocí nulové přípony. To může vést k neočekávaným výsledkům operace.

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
