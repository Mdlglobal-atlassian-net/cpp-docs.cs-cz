---
title: "Kompilátoru (úroveň 1) upozornění C4822 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4822
dev_langs:
- C++
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89ed0dc851726b7b543ed2b8e1a319cc2ac6756e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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