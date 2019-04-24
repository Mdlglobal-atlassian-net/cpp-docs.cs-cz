---
title: Kompilátor upozornění (úroveň 4) C4725
ms.date: 11/04/2016
f1_keywords:
- C4725
helpviewer_keywords:
- C4725
ms.assetid: effa0335-71c3-4b3b-8618-da4b9b46a95d
ms.openlocfilehash: 9da830133bbca2abcd5fa77339e698b35dae32f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325426"
---
# <a name="compiler-warning-level-4-c4725"></a>Kompilátor upozornění (úroveň 4) C4725

instrukce nemusí být na některých procesorech Pentium přesná.

Váš kód obsahuje instrukce vložené sestavení, která nemusí poskytovat přesné výsledky na některé mikroprocesory Pentium.

Následující ukázka generuje C4725:

```
// C4725.cpp
// compile with: /W4
// processor: x86
double m32fp = 2.0003e-17;

void f() {
   __asm
   {
      FDIV m32fp   // C4725
   }
}

int main() {
}
```