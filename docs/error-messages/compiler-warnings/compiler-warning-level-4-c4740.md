---
title: "Kompilátoru (úroveň 4) upozornění C4740 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4740
dev_langs: C++
helpviewer_keywords: C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 29337ebb07865d470ae60316e11f0eea2dce21d0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4740"></a>C4740 kompilátoru upozornění (úroveň 4)
tok nebo zrušení vloženého kódu asm potlačí globální optimalizace  
  
 Pokud je přechod v na nebo z `asm` bloku globální optimalizace jsou pro tuto funkci zakázán.  
  
 Následující ukázka generuje C4740:  
  
```  
// C4740.cpp  
// compile with: /O2 /W4  
// processor: x86  
int main() {  
   __asm jmp tester  
   tester:;  
}  
```