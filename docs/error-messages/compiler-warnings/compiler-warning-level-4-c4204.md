---
title: "Kompilátoru (úroveň 4) upozornění C4204 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4204
dev_langs: C++
helpviewer_keywords: C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: defdacf0de90248e0cd91a4a5d12fdbec42a9320
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4204"></a>C4204 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: agregační inicializátoru není konstantní.  
  
 Rozšíření Microsoft (/Ze) můžete provést inicializaci agregované typy (pole, struktury, sjednocení a třídy) s hodnotami, které nejsou konstanty.  
  
## <a name="example"></a>Příklad  
  
```  
// C4204.c  
// compile with: /W4  
int func1()  
{  
   return 0;  
}  
struct S1  
{  
   int i;  
};  
  
int main()  
{  
   struct S1 s1 = { func1() };   // C4204  
   return s1.i;  
}  
```  
  
 Takové inicializacích jsou neplatné v části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).