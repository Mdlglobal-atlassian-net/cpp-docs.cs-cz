---
title: "Kompilátoru (úroveň 1) upozornění C4401 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4401
dev_langs: C++
helpviewer_keywords: C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cabb50ca025390cd00f4c9db68f3aa97d606fa57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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