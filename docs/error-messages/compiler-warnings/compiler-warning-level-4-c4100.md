---
title: "Kompilátoru (úroveň 4) upozornění C4100 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4100
dev_langs: C++
helpviewer_keywords: C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5c3bf13b16b66550a37faf2bcd024f17d3e85421
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4100"></a>C4100 kompilátoru upozornění (úroveň 4)
"identifikátor": neregistrované formální parametr  
  
 Typ formálního parametru neodkazuje v těle funkce. Parametr neregistrované se ignoruje.  
  
 C4100 může být při kód volání destruktoru na vydaný jinak které se neodkazuje parametr primitivního typu.  Jedná se o omezení kompilátoru Visual C++.  
  
 Následující ukázka generuje C4100:  
  
```  
// C4100.cpp  
// compile with: /W4  
void func(int i) {   // C4100, delete the unreferenced parameter to  
                     //resolve the warning  
   // i;   // or, add a reference like this  
}  
  
int main()  
{  
   func(1);  
}  
```