---
title: Kompilátoru (úroveň 4) upozornění C4127 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4127
dev_langs:
- C++
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c98b2eb42cfc66c27faf74c3d6e46e981851a0a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293644"
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