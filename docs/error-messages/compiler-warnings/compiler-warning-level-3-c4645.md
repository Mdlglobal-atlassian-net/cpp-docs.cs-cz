---
title: "Kompilátoru (úroveň 3) upozornění C4645 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4645
dev_langs: C++
helpviewer_keywords: C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c327aa47f46ffa7d7533d818d5140fdc5a5933af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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