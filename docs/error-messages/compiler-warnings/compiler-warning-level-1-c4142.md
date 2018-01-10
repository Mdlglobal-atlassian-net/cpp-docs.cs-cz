---
title: "Kompilátoru (úroveň 1) upozornění C4142 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4142
dev_langs: C++
helpviewer_keywords: C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 73d3ad63aaf040b83622720040adf3a291d354e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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