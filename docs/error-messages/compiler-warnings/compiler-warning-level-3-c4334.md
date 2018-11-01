---
title: Kompilátor upozornění (úroveň 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: 55512bf28c8c20512d0d245810d3e5c1fec36939
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600691"
---
# <a name="compiler-warning-level-3-c4334"></a>Kompilátor upozornění (úroveň 3) C4334

'operator': výsledek 32bitového posunu se implicitně převedl na 64 bitů (byl 64bitový posun určený?)

Výsledek 32bitového posunu se implicitně převést na 64 bitů a kompilátoru podezření, že byl 64bitový posun určený.  Pokud chcete vyřešit toto upozornění, použijte 64bitový posun nebo explicitně přetypovat shift výsledek na 64bitovou verzi.

## <a name="example"></a>Příklad

Následující ukázka generuje C4334.

```
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```