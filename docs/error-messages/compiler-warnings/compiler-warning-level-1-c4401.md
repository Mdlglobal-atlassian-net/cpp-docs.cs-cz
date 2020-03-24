---
title: Upozornění kompilátoru (úroveň 1) C4401
ms.date: 11/04/2016
f1_keywords:
- C4401
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
ms.openlocfilehash: fe08509a05eed00f7e7d492e723e873d05e451ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162657"
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
