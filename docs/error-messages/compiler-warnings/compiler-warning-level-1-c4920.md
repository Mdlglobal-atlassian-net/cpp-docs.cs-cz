---
title: "Kompilátoru (úroveň 1) upozornění C4920 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4920
dev_langs: C++
helpviewer_keywords: C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba6d3cc41299c5b4b4b9329168f814ab732f524f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4920"></a>C4920 kompilátoru upozornění (úroveň 1)
člen výčtu výčtu člen = hodnota již zobrazená v výčtu výčtu jako člen = hodnota  
  
 Pokud .tlb, který můžete předat #import má stejné symbol definované ve dvou nebo více výčty, toto upozornění označuje, že následné identické symboly jsou ignorovány a bude okomentován se v souboru .tlh.  
  
 Za předpokladu, že .tlb, který obsahuje:  
  
```  
library MyLib  
{  
    typedef enum {  
        enumMember = 512  
    } AProblem;  
  
    typedef enum {  
        enumMember = 1024  
    } BProblem;  
};  
```  
  
 Následující ukázky generuje C4920,  
  
```  
// C4920.cpp  
// compile with: /W1  
#import "t4920.tlb"   // C4920  
  
int main() {  
}  
```