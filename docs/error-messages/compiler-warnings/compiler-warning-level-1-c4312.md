---
title: Kompilátoru (úroveň 1) upozornění C4312 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4312
dev_langs:
- C++
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18039e44a5616330c66603e448bcafd6d18ff7aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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