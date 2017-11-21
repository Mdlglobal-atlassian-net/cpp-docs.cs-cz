---
title: "Kompilátoru (úroveň 1) upozornění C4733 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4733
dev_langs: C++
helpviewer_keywords: C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0fc99bf8c0d3397a11b6e0b06c582a81dd2b4875
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4733"></a>C4733 kompilátoru upozornění (úroveň 1)
Vložené asm přiřazení k 'FS:0': není registrován jako bezpečné obslužné rutiny obslužná rutina  
  
 Funkce Úprava hodnoty v FS:0 přidat novou obslužnou rutinu výjimky nemusí fungovat s bezpečné výjimkami, protože obslužná rutina pravděpodobně není registrován jako obslužná rutina platné výjimky (viz [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)).  
  
 Toto upozornění vyřešíte buď odeberte definici FS:0 nebo tento vypnout upozornění a použít [. SAFESEH](../../assembler/masm/dot-safeseh.md) k určení obslužné rutiny bezpečné výjimek.  
  
 Následující ukázka generuje C4733:  
  
```  
// C4733.cpp  
// compile with: /W1 /c  
// processor: x86  
#include "stdlib.h"  
#include "stdio.h"  
void my_handler()  
{  
   printf("Hello from my_handler\n");  
   exit(1);  
}  
  
int main()  
{  
   _asm {  
      push    my_handler  
      mov     eax, DWORD PTR fs:0  
      push    eax  
      mov     DWORD PTR fs:0, esp   // C4733  
   }  
  
   *(int*)0 = 0;  
}  
```