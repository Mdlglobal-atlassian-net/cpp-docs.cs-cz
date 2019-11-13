---
title: Upozornění kompilátoru (úroveň 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: ebebfe9994be3dd136e3924cb2aea60c0c901926
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051634"
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