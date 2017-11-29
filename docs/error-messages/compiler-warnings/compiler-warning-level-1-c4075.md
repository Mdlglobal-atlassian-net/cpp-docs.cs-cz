---
title: "Kompilátoru (úroveň 1) upozornění C4075 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4075
dev_langs: C++
helpviewer_keywords: C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba20ea087de69afa5c73ff32d6b74dd6a27652ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4075"></a>C4075 kompilátoru upozornění (úroveň 1)
Inicializátory put v oblasti nerozpoznané inicializace  
  
 A [init_seg – #pragma](../../preprocessor/init-seg.md) používá název nerozpoznané části. Kompilátor ignoruje **– Direktiva pragma** příkaz.  
  
 Následující ukázka generuje C4075:  
  
```  
// C4075.cpp  
// compile with: /W1  
#pragma init_seg("mysegg")   // C4075  
  
// try..  
// #pragma init_seg(user)  
  
int main() {  
}  
```