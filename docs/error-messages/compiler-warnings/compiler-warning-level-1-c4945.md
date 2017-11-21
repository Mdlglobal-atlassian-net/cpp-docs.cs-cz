---
title: "Kompilátoru (úroveň 1) upozornění C4945 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4945
dev_langs: C++
helpviewer_keywords: C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b8c42a0a021f1bbe7399fa9fa8564739574b5b28
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4945"></a>C4945 kompilátoru upozornění (úroveň 1)
'symbol': nelze importovat symbol 'assembly2': jako 'symbol' již byla naimportována ze sestavení 'assembly1'  
  
 Symbol byla naimportována ze odkazované sestavení, ale tento symbol se už importoval z jiného odkazované sestavení. Buď odkazovat na jedno ze sestavení nebo získání názvu symbolu změnit v jednom sestavení.  
  
 Následující ukázky generovat C4945.  
  
```  
// C4945a.cs  
// compile with: /target:library  
// C# source code to create a dll  
public class ClassA {  
   public int i;  
}  
```  
  
 A pak  
  
```  
// C4945b.cs  
// compile with: /target:library  
// C# source code to create a dll  
public class ClassA {  
   public int i;  
}  
```  
  
 A pak  
  
```  
// C4945c.cpp  
// compile with: /clr /LD /W1  
#using "C4945a.dll"  
#using "C4945b.dll"   // C4945  
```