---
title: Kompilátor upozornění (úroveň 4) C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 936dfb5464eabe7b1ac44df24445224fb9e204a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457881"
---
# <a name="compiler-warning-level-4-c4740"></a>Kompilátor upozornění (úroveň 4) C4740

Flow nebo z vloženého kódu asm potlačuje globální optimalizaci.

Když je nárůst v na nebo z `asm` bloku, globální optimalizace zakázány pro tuto funkci.

Následující ukázka generuje C4740:

```
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```