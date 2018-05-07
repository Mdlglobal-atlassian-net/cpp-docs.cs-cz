---
title: C4936 upozornění kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4936
dev_langs:
- C++
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcf9f32a4a1b1e43cb4bd69c754e3ae3a98bff3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4936"></a>C4936 upozornění kompilátoru
Tato __declspec je podporována pouze, když kompilujete s/CLR nebo/CLR: pure  
  
 **/CLR: pure** – možnost kompilátoru je zastaralá ve Visual Studiu 2015.  
  
 A `__declspec` ale který byl použit modifikátor `__declspec` modifikátor platí, pouze když kompilujete s jedním z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) možnosti.  
  
 Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [proces](../../cpp/process.md).  
  
 C4936 je vždy vydané jako chyba.  Můžete zakázat C4936 s [upozornění](../../preprocessor/warning.md) – Direktiva pragma.  
  
 Následující ukázka generuje C4936:  
  
```  
// C4936.cpp  
// compile with: /c  
// #pragma warning (disable : 4936)  
__declspec(process) int i;   // C4936  
__declspec(appdomain) int j;   // C4936  
```