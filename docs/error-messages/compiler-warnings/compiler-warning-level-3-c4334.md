---
title: Upozornění kompilátoru (úroveň 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: 38b93c83f822bc5b856a46f0dd62ea275d2bf207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198715"
---
# <a name="compiler-warning-level-3-c4334"></a>Upozornění kompilátoru (úroveň 3) C4334

' operator ': výsledek 32-bitového posunu byl implicitně převeden na 64 bity (bylo 64-bitové posunutí zamýšlené?)

Výsledek 32. bit Shift byl implicitně převeden na 64-bity a kompilátor má za následek, že byl záměr 64-bit.  Chcete-li vyřešit toto upozornění, buď použijte 64. bit Shift, nebo explicitně přetypujte výsledek posunutí na 64-bit.

## <a name="example"></a>Příklad

Následující ukázka generuje C4334.

```cpp
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```
