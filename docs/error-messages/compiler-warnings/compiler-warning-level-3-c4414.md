---
title: Kompilátoru (úroveň 3) upozornění C4414 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4414
dev_langs:
- C++
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1526b20732d7a1b08ec8d753cb64e33e42dd809
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4414"></a>C4414 kompilátoru upozornění (úroveň 3)
'function': krátké přechod na funkce převést na téměř  
  
 Krátký přeskočí generovat compact instrukce, které větví na adresu v rámci omezeným rozsahem z pokynů. Pokyn zahrnuje krátký posun, který představuje vzdálenost mezi přechod a cílová adresa, v definici funkce. Při propojování funkce může být přesunutý nebo mohou podléhat propojování optimalizace, které způsobí funkce se má přesunout mimo rozsah dosažitelný z krátký posun. Kompilátor musíte vygenerovat speciální záznam pro přechod, který vyžaduje skok pokyn BLÍZKÉ nebo DALEKO. Kompilátor provedené převod.  
  
 Například následující kód generuje C4414:  
  
```  
// C4414.cpp  
// compile with: /W3 /c  
// processor: x86  
int DoParityEven();  
int DoParityOdd();  
unsigned char global;  
int __declspec(naked) DoParityEither()  
{  
   __asm  
   {  
      test global,0  
      jpe SHORT DoParityEven  // C4414  
      jmp SHORT DoParityOdd   // C4414  
   }  
}  
```