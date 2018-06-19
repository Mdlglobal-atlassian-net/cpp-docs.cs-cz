---
title: Kompilátoru (úroveň 1) upozornění C4822 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4822
dev_langs:
- C++
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9491d522c65eba3599c3618d510c57b55682876
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283014"
---
# <a name="compiler-warning-level-1-c4822"></a>C4822 kompilátoru upozornění (úroveň 1)
"člen": místní třídy – členská funkce nemá text  
  
 Členské funkce místní třídy byl deklarován ale není definovaný ve třídě. Pokud chcete použít místní třídy členské funkce, musí být definovat ve třídě. Nelze deklarovat ve třídě a definování mimo třídy.  
  
 Všechny definice na více systémů třídy pro místní třídy členské funkce bude k chybě.  
  
 Následující ukázka generuje C4822:  
  
```  
// C4822.cpp  
// compile with: /W1  
int main() {  
   struct C {  
      void func1(int);   // C4822  
      // try the following line instead  
      // void func1(int){}  
  };  
}  
```