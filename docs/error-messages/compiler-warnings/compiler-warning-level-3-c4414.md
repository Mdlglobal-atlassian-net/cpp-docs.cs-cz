---
title: "Kompilátoru (úroveň 3) upozornění C4414 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4414
dev_langs: C++
helpviewer_keywords: C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 90644170953976d0fb661f1491b59915d5dd3667
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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