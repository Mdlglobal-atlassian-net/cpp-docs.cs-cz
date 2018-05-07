---
title: Kompilátoru (úroveň 1) upozornění C4177 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4177
dev_langs:
- C++
helpviewer_keywords:
- C4177
ms.assetid: 2b05a5b3-696e-4f21-818e-227b9335e748
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae001b593d965ead0c834793dbbeee3972a5b0bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4177"></a>C4177 kompilátoru upozornění (úroveň 1)
\#pragma – Direktiva pragma by měla být v globálním oboru  
  
 [– Direktiva pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) – Direktiva pragma by se neměla používat v rámci místního oboru. **– Direktiva pragma** nebude platný až do globální obor po aktuálním oboru.  
  
 Následující ukázka generuje C4177:  
  
```  
// C4177.cpp  
// compile with: /W1  
// #pragma bss_seg("global")   // OK  
  
int main() {  
   #pragma bss_seg("local")    // C4177  
}  
```