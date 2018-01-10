---
title: "Kompilátoru (úroveň 1) upozornění C4558 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4558
dev_langs: C++
helpviewer_keywords: C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a9e207bb188bdfa31ef1625aa5e1b607823e755e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4558"></a>C4558 kompilátoru upozornění (úroveň 1)
Hodnota operand 'Hodnota' je mimo rozsah 'dolní hranice - horní hranice.  
  
 Hodnota předaná instrukce jazyk sestavení je mimo rozsah zadaný pro parametr. Hodnota bude zkrácen.  
  
 Následující ukázka generuje C4558:  
  
```  
// C4558.cpp  
// compile with: /W1  
// processor: x86  
void asm_test() {  
   __asm pinsrw   mm1, eax, 8;   // C4558  
}  
  
int main() {  
}  
```