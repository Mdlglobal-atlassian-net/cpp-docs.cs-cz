---
title: Kompilátoru (úroveň 1) upozornění C4717 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4717
dev_langs:
- C++
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa953d8d41003ff53e721671845c1ddee26da640
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4717"></a>C4717 kompilátoru upozornění (úroveň 1)
'function': rekurzivní u všech cest řízení funkce způsobí přetečení zásobníku modul runtime  
  
 Každý cesta prostřednictvím funkce obsahuje volání funkce. Vzhledem k tomu, že neexistuje žádný způsob, jak ukončit rekurzivní funkce bez první volání sám sebe, se nikdy zavře funkce.  
  
 Následující ukázka generuje C4717:  
  
```  
// C4717.cpp  
// compile with: /W1 /c  
// C4717 expected  
int func(int x) {  
   if (x > 1)  
      return func(x - 1); // recursive call  
   else {  
      int y = func(0) + 1; // recursive call  
      return y;  
   }  
}  
  
int main(){  
   func(1);  
}  
```