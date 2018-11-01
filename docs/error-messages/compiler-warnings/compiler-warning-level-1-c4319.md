---
title: Kompilátor upozornění (úroveň 1) C4319
ms.date: 1/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: 20b268bacd6e7e259e9b4fa1c9e98fa6fd353718
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599443"
---
# <a name="compiler-warning-level-1-c4319"></a>Kompilátor upozornění (úroveň 1) C4319

> "~": nulové rozšíření "*type1*"do"*type2*' větší velikosti

Výsledkem **~** – operátor (bitový doplněk) je bez znaménka a pak rozšířit nula je převedena na typ větší.

## <a name="example"></a>Příklad

V následujícím příkladu `~(a - 1)` je vyhodnocen jako výraz unsigned long 32bitová verze a následně převeden do 64 bitů nulové rozšíření. To může vést k výsledkům neočekávaná operace.

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
