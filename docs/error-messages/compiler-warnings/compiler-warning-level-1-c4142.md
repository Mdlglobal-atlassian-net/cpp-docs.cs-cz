---
title: Kompilátoru (úroveň 1) upozornění C4142 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4142
dev_langs:
- C++
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c87b7689cf11ab28c1a6377ff85e1594fd1b5fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4142"></a>C4142 kompilátoru upozornění (úroveň 1)
neškodné předefinování typu  
  
 Typ je předefinovat způsobem, který nemá žádný vliv na generovaného kódu.  
  
 Chcete-li vyřešit kontrolou následující možné příčiny:  
  
-   Členské funkce odvozené třídy má jiný typ vrácené z odpovídající členská funkce základní třídy.  
  
-   Typ definovaný s `typedef` příkaz je předefinovat pomocí různých syntaxe.  
  
 Následující ukázka generuje C4142:  
  
```  
// C4142.c  
// compile with: /W1  
float X2;  
X2 = 2.0 + 1.0;   // C4142  
  
int main() {  
   float X2;  
   X2 = 2.0 + 1.0;   // OK  
}  
```