---
title: Upozornění kompilátoru (úroveň 1) C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: 39674c32deb506725aa5f7c1f5f875e771519938
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185669"
---
# <a name="compiler-warning-level-1-c4733"></a>Upozornění kompilátoru (úroveň 1) C4733

Vložené ASM přiřadí se k FS: 0: obslužná rutina není zaregistrovaná jako bezpečná obslužná rutina.

Funkce, která upravuje hodnotu v FS: 0 Chcete-li přidat novou obslužnou rutinu výjimky, nemusí fungovat s bezpečnými výjimkami, protože obslužná rutina nemusí být registrována jako platná obslužná rutina výjimky (viz [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)).

Chcete-li vyřešit toto upozornění, odstraňte FS: 0. Zakažte nebo vypněte toto upozornění a použijte [. SAFESEH](../../assembler/masm/dot-safeseh.md) pro určení bezpečných obslužných rutin výjimek.

Následující ukázka generuje C4733:

```cpp
// C4733.cpp
// compile with: /W1 /c
// processor: x86
#include "stdlib.h"
#include "stdio.h"
void my_handler()
{
   printf("Hello from my_handler\n");
   exit(1);
}

int main()
{
   _asm {
      push    my_handler
      mov     eax, DWORD PTR fs:0
      push    eax
      mov     DWORD PTR fs:0, esp   // C4733
   }

   *(int*)0 = 0;
}
```
