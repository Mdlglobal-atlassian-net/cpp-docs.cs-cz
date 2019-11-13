---
title: Upozornění kompilátoru (úroveň 1) C4401
ms.date: 11/04/2016
f1_keywords:
- C4401
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
ms.openlocfilehash: 242c854339608c88d139c898d81d142c52f90134
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966319"
---
# <a name="compiler-warning-level-1-c4401"></a>Upozornění kompilátoru (úroveň 1) C4401

' bitového pole ': člen je bitové pole

Kód vloženého sestavení se pokusí o přístup k členu bitového pole. Vložené sestavení nemůže přistupovat ke členům bitových polí, takže se použije poslední hranice balení před členem bitového pole.

Chcete-li se tomuto upozornění vyhnout, přetypování bitového pole na příslušný typ před vytvořením odkazu ve vloženém kódu sestavení. Následující ukázka generuje C4401:

```cpp
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