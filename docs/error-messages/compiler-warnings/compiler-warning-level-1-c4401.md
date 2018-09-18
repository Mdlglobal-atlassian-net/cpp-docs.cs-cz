---
title: Upozornění (úroveň 1) C4401 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4401
dev_langs:
- C++
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f9f7bfcf826b9bda4232a8f4068d8be45dc3ab5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043544"
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