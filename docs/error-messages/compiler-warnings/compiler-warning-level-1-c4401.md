---
title: Kompilátor upozornění (úroveň 1) C4401
ms.date: 11/04/2016
f1_keywords:
- C4401
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
ms.openlocfilehash: c7e6cf8a52288d895b74481678dc91fee387a6a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455416"
---
# <a name="compiler-warning-level-1-c4401"></a>Kompilátor upozornění (úroveň 1) C4401

"bitového pole": člen je bitové pole.

Vložený kód sestavení pokusí o přístup ke členu bitového pole. Vložené sestavení nemá přístup k členy bitových polí, takže poslední hranici balení před členem bitové pole se používá.

K tomuto upozornění předejít, přetypování bitového pole s typem odpovídající před odkazu v vložený kód sestavení. Následující ukázka generuje C4401:

```
// C4401.cpp
// compile with: /W1
// processor: x86
typedef struct bitfield {
   signed bit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bf.bit = 0;
   __asm {
      mov bf.bit,0;   // C4401
   }

   /* use the following __asm block to resolve the warning
   int i = (int)bf.bit;
   __asm {
      mov i,0;
   }
   */
}
```