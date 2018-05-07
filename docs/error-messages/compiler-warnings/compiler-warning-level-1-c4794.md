---
title: Kompilátoru (úroveň 1) upozornění C4794 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4794
dev_langs:
- C++
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88ffa1200e7c760f028549335f0df5a9ea8ba3d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4794"></a>C4794 kompilátoru upozornění (úroveň 1)
segment proměnné místní úložiště vláken "proměnné" změněn z "název části" na ".tls$.  
  
 Jste použili [#pragma data_seg](../../preprocessor/data-seg.md) uvést proměnnou tls v části není počínaje .tls$.  
  
 .Tls$*x* části bude existovat v souboru objektu kde [__declspec(thread)](../../cpp/thread.md) proměnné jsou definovány. .Tls oddíl v souboru EXE nebo DLL, bude z těchto částí.  
  
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