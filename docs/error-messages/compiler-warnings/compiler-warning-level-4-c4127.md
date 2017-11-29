---
title: "Kompilátoru (úroveň 4) upozornění C4127 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4127
dev_langs: C++
helpviewer_keywords: C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 711543436c39f00da9fa754cf8a60349b51ab84b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4127"></a>C4127 kompilátoru upozornění (úroveň 4)
podmíněným výrazem je konstant  
  
 Řízení výraz `if` příkaz nebo `while` smyčky vyhodnocen jako konstanta. Kvůli jejich běžné idiomatickou využití, například 1 trivial konstanty nebo `true` nespouštějí upozornění, pokud se nejedná o výsledek operace ve výrazu. Pokud řízení výraz `while` smyčky je konstanta, protože opakování ve smyčce ukončeno uprostřed, zvažte nahrazení `while` cykly s `for` smyčky. Můžete vynechat inicializace, testovací ukončení a cykly přírůstek `for` ve smyčce, což způsobí, že smyčky být nekonečné, stejně jako `while(1)`, a můžete ukončit smyčky z textu `for` příkaz.  
  
 Následující příklad ukazuje dva způsoby C4127 se generuje a ukazuje, jak používat pro smyčky, aby se zabránilo upozornění:  
  
```  
// C4127.cpp  
// compile with: /W4  
#include <stdio.h>  
int main() {  
   if (1 == 1) {}   // C4127  
   while (42) { break; }   // C4127  
  
   // OK  
   for ( ; ; ) {  
      printf("test\n");  
      break;  
   }  
}  
```