---
title: "C2626 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2626
dev_langs: C++
helpviewer_keywords: C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 54cee1b985f53e25a0ceb2426231440f1a1bd9bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2626"></a>C2626 chyby kompilátoru
"identifikátor": privátní nebo chráněný datový člen není povolen v anonymní struktura nebo sjednocení  
  
 Člen anonymní struktura nebo sjednocení musí mít veřejný přístup.  
  
 Následující ukázka generuje C2626:  
  
```  
// C2626.cpp  
int main() {  
   union {  
   protected:  
      int j;     // C2626, j is protected  
   private:  
      int k;     // C2626, k is private  
   };  
}  
```  
  
 Pokud chcete tento problém vyřešit, odeberte všechny soukromé nebo chráněné značky:  
  
```  
// C2626b.cpp  
int main() {  
   union {  
   public:  
      int i;   // OK, i is public  
   };  
}  
```