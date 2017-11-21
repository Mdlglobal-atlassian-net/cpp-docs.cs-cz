---
title: "Kompilátoru (úroveň 1) upozornění C4145 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4145
dev_langs: C++
helpviewer_keywords: C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0e74e512512cd9eb97e4693aec71f33eee6002a5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4145"></a>C4145 kompilátoru upozornění (úroveň 1)
'expression1': relační výraz jako výraz přepínače; možnost záměny s 'Výraz2.  
  
 A `switch` příkaz používá relační výraz jako ovládací prvek výraz, jehož výsledkem je logická hodnota pro **případ** příkazy. Měli jste na mysli *Výraz2*?  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4145:  
  
```  
// C4145.cpp  
// compile with: /W1  
int main() {  
   int i = 0;  
   switch(i == 1) {   // C4145, use i instead of i == 1 to resolve  
      case 1:  
         break;  
      default:  
         break;  
   }  
}  
```