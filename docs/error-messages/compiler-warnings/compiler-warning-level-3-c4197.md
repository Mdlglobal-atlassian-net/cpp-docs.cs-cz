---
title: Upozornění kompilátoru (úroveň 3) C4197
ms.date: 11/04/2016
f1_keywords:
- C4197
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
ms.openlocfilehash: fbc3fbf7f7408f854b1de969688dfbd25e826d84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161591"
---
# <a name="compiler-warning-level-3-c4197"></a>Upozornění kompilátoru (úroveň 3) C4197

Typ: volatile na nejvyšší úrovni v přetypování se ignoruje.

Kompilátor zjistil přetypování na typ r-value, který je kvalifikován s typem [volatile](../../cpp/volatile-cpp.md), nebo přetypování typu r-hodnota na nějaký typ, který je kvalifikován jako volatile. Podle standardu jazyka C (6.5.3) jsou vlastnosti přidružené k kvalifikovaným typům smysluplné jenom pro výrazy l-value.

Následující ukázka generuje C4197:

```cpp
// C4197.cpp
// compile with: /W3
#include <stdio.h>
#include <signal.h>
#include <stdlib.h>

void sigproc(int);
struct S
{
   int i;
} s;

int main()
{
   signal(SIGINT, sigproc);
   s.i = 1;
   S *pS = &s;
   for ( ; (volatile int)pS->i ; )   // C4197
      break;
   // for ( ; *(volatile int *)&pS->i ; )   // OK
   //    break;
}

void sigproc(int) // ctrl-C
{
   signal(SIGINT, sigproc);
   s.i = 0;
}
```
