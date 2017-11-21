---
title: "Kompilátoru (úroveň 3) upozornění C4197 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4197
dev_langs: C++
helpviewer_keywords: C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 08ad91be08a3690e6505a252eb6559d274e2f3ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4197"></a>C4197 kompilátoru upozornění (úroveň 3)
'type': nejvyšší úrovně volatile v přetypování je ignorována.  
  
 Kompilátor zjistil přetypování na typ r-value, což je kvalifikovaný s [volatile](../../cpp/volatile-cpp.md), nebo přetypování typu r-value na nějaký typ, který je kvalifikovaný s volatile. Podle C standardní (6.5.3) dávat smysl jenom pro výrazy hodnot l vlastnosti související s kvalifikovaný typy.  
  
 Následující ukázka generuje C4197:  
  
```  
// C4197.cpp  
// compile with: /W3  
#include <stdio.h>  
#include <signal.h>  
#include <stdlib.h>  
  
void sigproc(int);  
struct S  
{  
   int i;  
} s;  
  
int main()  
{  
   signal(SIGINT, sigproc);  
   s.i = 1;  
   S *pS = &s;  
   for ( ; (volatile int)pS->i ; )   // C4197  
      break;  
   // for ( ; *(volatile int *)&pS->i ; )   // OK  
   //    break;  
}  
  
void sigproc(int) // ctrl-C  
{  
   signal(SIGINT, sigproc);  
   s.i = 0;  
}  
  
```