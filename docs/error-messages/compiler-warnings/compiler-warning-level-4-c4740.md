---
title: Upozornění kompilátoru (úroveň 4) C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 679f577eb7911b401473ee570e367ed5a8a094eb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989485"
---
# <a name="compiler-warning-level-4-c4740"></a>Upozornění kompilátoru (úroveň 4) C4740

tok ve vloženém kódu ASM nebo z něj potlačuje globální optimalizaci.

Pokud dojde k přechodu do nebo ven z `asm` bloku, globální optimalizace jsou pro tuto funkci zakázané.

Následující ukázka generuje C4740:

```cpp
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```
