---
title: Chyba kompilátoru C2849
ms.date: 11/04/2016
f1_keywords:
- C2849
helpviewer_keywords:
- C2849
ms.assetid: e28f6b3e-e0e7-4f92-b006-ebaa81d368e6
ms.openlocfilehash: 4812c836d099e9cbb3849e48046edfdeda24ffc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594698"
---
# <a name="compiler-error-c2849"></a>Chyba kompilátoru C2849

"destruktoru": rozhraní nemůže mít destruktor

Visual C++ [rozhraní](../../cpp/interface.md) nemůže mít destruktor.

Následující ukázka generuje C2849:

```
// C2849.cpp
// compile with: /c
__interface C {
   ~C();   // C2849 destructor not allowed in an interface
};
```