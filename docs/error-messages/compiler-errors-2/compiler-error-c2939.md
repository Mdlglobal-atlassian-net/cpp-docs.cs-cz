---
title: "C2939 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2939
dev_langs: C++
helpviewer_keywords: C2939
ms.assetid: 455b050b-f2dc-4b5b-bd6a-e1f81d3d1644
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fbe4bb402755f421996edabfb9dffb43edf65228
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2939"></a>C2939 chyby kompilátoru
'class': id – třída typu předefinovat jako proměnnou a místní data  
  
 Třídu generic nebo šablonu nelze použít jako proměnnou místní data.  
  
 Tato chyba může být způsobena Pokud nesprávně se splní složené závorky.  
  
 Následující ukázka generuje C2939:  
  
```  
// C2939.cpp  
template<class T>  
struct TC { };   
int main() {  
   int TC<int>;   // C2939  
   int TC;   // OK  
}  
```  
  
 C2939 může dojít také při použití obecných typů:  
  
```  
// C2939b.cpp  
// compile with: /clr  
generic<class T>  
ref struct GC { };  
  
int main() {  
   int GC<int>;   // C2939  
   int GC;   // OK  
}  
```