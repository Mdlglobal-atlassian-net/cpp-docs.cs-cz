---
title: Kompilátoru (úroveň 3) upozornění C4645 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4645
dev_langs:
- C++
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 718afb6b8336e36e0c0244cbdccd8af16ac4167f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4645"></a>C4645 kompilátoru upozornění (úroveň 3)
funkce deklarovat s __declspec(noreturn) má příkaz return  
  
 A [vrátit](../../cpp/return-statement-in-program-termination-cpp.md) příkaz byl nalezen ve funkci, která je označena [noreturn](../../cpp/noreturn.md) `__declspec` modifikátor. `return` Příkaz byl ignorován.  
  
 Následující ukázka generuje C4645:  
  
```  
// C4645.cpp  
// compile with:  /W3  
void __declspec(noreturn) func() {  
   return;   // C4645, delete this line to resolve  
}  
  
int main() {  
}  
```