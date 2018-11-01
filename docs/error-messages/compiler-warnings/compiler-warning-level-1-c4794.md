---
title: Kompilátor upozornění (úroveň 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: d44e3af88de9457fdc5c2df905ccbae22d3562da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464074"
---
# <a name="compiler-warning-level-1-c4794"></a>Kompilátor upozornění (úroveň 1) C4794

segment proměnné místní úložiště vláken "proměnné" změněno z "název oddílu" na ".tls$"

Použili jste [#pragma data_seg](../../preprocessor/data-seg.md) chcete změnit proměnné tls na oddíl .tls $ nespouští.

.Tls$*x* části bude existovat do souboru objektu kde [__declspec(thread)](../../cpp/thread.md) proměnné jsou definovány. Oddíl .tls v souboru EXE nebo DLL způsobí z těchto oddílů.

## <a name="example"></a>Příklad

Následující ukázka generuje C4794:

```
// C4794.cpp
// compile with: /W1 /c
#pragma data_seg(".someseg")
__declspec(thread) int i;   // C4794

// OK
#pragma data_seg(".tls$9")
__declspec(thread) int j;
```