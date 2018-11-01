---
title: Chyba kompilátoru C2184
ms.date: 11/04/2016
f1_keywords:
- C2184
helpviewer_keywords:
- C2184
ms.assetid: 80fc8bff-7d76-4bde-94d2-01d84bb6824a
ms.openlocfilehash: 146035134cc159b9e4271ce10c94f196098581b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639969"
---
# <a name="compiler-error-c2184"></a>Chyba kompilátoru C2184

'type': Neplatný typ pro možnost __except výrazu, musí být integrální

Typ použila [__except](../../c-language/try-except-statement-c.md) příkazu, ale typ není povolený.

Následující ukázka generuje C2184:

```
// C2184.cpp
void f() {
   int * p;
   __try{}
   __except(p){};   // C2184
}
```

Možná řešení:

```
// C2184b.cpp
// compile with: /c
void f() {
   int i = 0;
   __try{}
   __except(i){};
}
```