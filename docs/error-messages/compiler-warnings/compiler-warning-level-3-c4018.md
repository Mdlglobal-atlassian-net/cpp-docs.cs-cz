---
title: "Kompilátoru (úroveň 3) upozornění C4018 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4018
dev_langs: C++
helpviewer_keywords: C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f409075947d6151c643f477513986b6dee50ee65
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4018"></a>C4018 kompilátoru upozornění (úroveň 3)
"výrazu": Neshoda podepsané nepodepsaných  
  
 Porovnání číslo signed a unsigned vyžaduje kompilátor převést hodnotu podepsaného na nepodepsané.  
  
 Toto upozornění může být stanovena, pokud jeden z těchto dvou typů přetypovat při testování signed a unsigned typy.  
  
 Následující ukázka generuje C4018:  
  
```  
// C4018.cpp  
// compile with: /W3  
int main() {  
   unsigned int uc = 0;  
   int c = 0;  
   unsigned int c2 = 0;  
  
   if (uc < c) uc = 0;   // C4018  
  
   // OK  
   if (uc == c2) uc = 0;  
}  
```