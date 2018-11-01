---
title: Kompilátor upozornění (úroveň 1) C4384
ms.date: 11/04/2016
f1_keywords:
- C4384
helpviewer_keywords:
- C4384
ms.assetid: fafa8eb2-cbfc-4edb-8b0f-511ff5d37ac0
ms.openlocfilehash: 0f2666011e88dfd59eaaca154f4407bece7c963c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454684"
---
# <a name="compiler-warning-level-1-c4384"></a>Kompilátor upozornění (úroveň 1) C4384

\#direktivy pragma "make_public" by měl použít jenom u globálního rozsahu

[Make_public](../../preprocessor/make-public.md) – Direktiva pragma se použijí nesprávně.

## <a name="example"></a>Příklad

Následující ukázka generuje C4384.

```
// C4384.cpp
// compile with: /c /W1
namespace n {
   #pragma make_public(N::C)   // C4384
   namespace N {
      class C {};
   }
}
```