---
title: Upozornění (úroveň 1) C4312 kompilátoru | Dokumentace Microsoftu
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
ms.openlocfilehash: 8b30d020532935c925b1ecab25d17cd43a7e8663
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205899"
---
# <a name="compiler-warning-level-1-c4312"></a>Kompilátor upozornění (úroveň 1) C4312
'operation': převod z 'type1' na 'type2' větší velikosti  
  
 Toto upozornění zjistí pokus o přiřadí hodnotu 32 bitů 64bitového ukazatele typu, například přetypování 32-bit `int` nebo `long` na 64bitový ukazatel.  
  
 To může být potenciálně nebezpečný převod i pro ukazatel hodnot, které odpovídají v 32 bitů, pokud dojde k rozšířením znaménka. Pokud negativní 32bitové celé číslo je přiřazený k typu 64bitového ukazatele, rozšířením znaménka způsobí, že hodnota ukazatele odkazují na adresu paměti liší od hodnoty na celé číslo.  
  
 Jenom se objeví toto upozornění pro kompilaci 64-bit cíle. Další informace najdete v tématu [pravidla pro používání ukazatele](/windows/desktop/WinProg64/rules-for-using-pointers).  
  
 Následující příklad kódu generuje C4312 při kompilaci pro 64bitové cíle:  
  
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