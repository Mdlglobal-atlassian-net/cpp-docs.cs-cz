---
title: Kompilátor upozornění (úroveň 3) C4197
ms.date: 11/04/2016
f1_keywords:
- C4197
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
ms.openlocfilehash: 6de07411a51c8436356e044cb397a65513827fdf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442572"
---
# <a name="compiler-warning-level-3-c4197"></a>Kompilátor upozornění (úroveň 3) C4197

'type': volatile na nejvyšší úrovni v přetypování se ignoruje.

Kompilátor zjistil přetypování na r-value typu, který je kvalifikován [volatile](../../cpp/volatile-cpp.md), nebo výraz přetypování r-value typu pro nějaký typ, který je kvalifikován volatile. Podle jazyka C standard (6.5.3) jsou vlastnosti související s typy kvalifikovaný smysl jenom pro výrazy l hodnotou.

Následující ukázka generuje C4197:

```
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