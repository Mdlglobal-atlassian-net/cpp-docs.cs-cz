---
title: Upozornění kompilátoru (úroveň 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: 7f7ea7555937069caf5f83c9bf00f0fa980ef020
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175113"
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
