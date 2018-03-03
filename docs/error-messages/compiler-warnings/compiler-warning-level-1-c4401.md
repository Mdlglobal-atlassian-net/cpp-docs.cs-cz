---
title: "Kompilátoru (úroveň 1) upozornění C4401 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4401
dev_langs:
- C++
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b1042550b4ea176a314e174549ed560cd3ece025
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4401"></a>C4401 kompilátoru upozornění (úroveň 1)
'bitfield': člen je bitová pole  
  
 Kód vnořeného sestavení pokusí o přístup člena bitová pole. Vnořené sestavení nemá přístup k bitová pole členů, tak se používá poslední hranic okolních před člen bitové pole.  
  
 Abyste se vyhnuli toto upozornění, přetypování před provedením odkaz v kódu vnořeného sestavení pole bit do příslušného typu. Následující ukázka generuje C4401:  
  
```  
// C4401.cpp  
// compile with: /W1  
// processor: x86  
typedef struct bitfield {  
   signed bit : 1;  
} mybitfield;  
  
int main() {  
   mybitfield bf;  
   bf.bit = 0;  
   __asm {  
      mov bf.bit,0;   // C4401  
   }  
  
   /* use the following __asm block to resolve the warning  
   int i = (int)bf.bit;  
   __asm {  
      mov i,0;  
   }  
   */  
}  
```