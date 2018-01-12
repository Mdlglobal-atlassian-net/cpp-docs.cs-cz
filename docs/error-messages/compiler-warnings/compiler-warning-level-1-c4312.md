---
title: "Kompilátoru (úroveň 1) upozornění C4312 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4312
dev_langs: C++
helpviewer_keywords: C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a4e6fa46fe9b84b138fffedf206d08ffbb30790
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4312"></a>C4312 kompilátoru upozornění (úroveň 1)
'operation': převod z 'type1' na 'type2' větší velikosti  
  
 Toto upozornění zjistí pokus o přiřadit hodnotu 32-bit 64-bit ukazatel typu, například přetypování 32bitové `int` nebo `long` na 64-bit ukazatel.  
  
 To může být konverzi nezabezpečený i pro ukazatele hodnot, které odpovídají v 32bitová verze, když dojde k rozšíření přihlášení. Pokud záporné 32bitové celé číslo je přiřazen k 64-bit ukazatel typu, rozšíření přihlašovací způsobí, že hodnota ukazatele odkazovat na adresu paměti liší od hodnoty na celé číslo.  
  
 Pro 64bitové kompilace cíle pouze se objeví toto upozornění. Další informace najdete v tématu [pravidla pro používání ukazatele](http://msdn.microsoft.com/library/windows/desktop/aa384242).  
  
 Následující příklad kódu vytvoří C4312 při kompilaci pro 64bitové cíle:  
  
```  
// C4312.cpp  
// compile by using: cl /W1 /LD C4312.cpp  
void* f(int i) {  
   return (void*)i;   // C4312 for 64-bit targets  
}  
  
void* f2(__int64 i) {  
   return (void*)i;   // OK  
}  
```