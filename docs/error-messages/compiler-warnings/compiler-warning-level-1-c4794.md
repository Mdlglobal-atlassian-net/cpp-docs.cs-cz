---
title: Upozornění kompilátoru (úroveň 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: 7d669280c0dc6a730a22480e602dac8cc6153449
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052370"
---
# <a name="compiler-warning-level-1-c4794"></a>Upozornění kompilátoru (úroveň 1) C4794

segment thread local proměnné úložiště ' Variable ' se změnil z ' název oddílu ' na '. TLS $ '

Použili jste [#pragma data_seg](../../preprocessor/data-seg.md) k umístění proměnné TLS do oddílu, který nezačíná na. TLS $.

Oddíl. TLS $*x* bude existovat v souboru objektu, kde jsou definovány proměnné [__declspec (thread)](../../cpp/thread.md) . V části. TLS v souboru EXE nebo DLL bude výsledkem tyto části.

## <a name="example"></a>Příklad

Následující ukázka generuje C4794:

```cpp
// C4794.cpp
// compile with: /W1 /c
#pragma data_seg(".someseg")
__declspec(thread) int i;   // C4794

// OK
#pragma data_seg(".tls$9")
__declspec(thread) int j;
```