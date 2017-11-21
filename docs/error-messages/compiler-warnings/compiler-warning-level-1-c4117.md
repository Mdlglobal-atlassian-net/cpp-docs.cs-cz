---
title: "Kompilátoru (úroveň 1) upozornění C4117 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4117
dev_langs: C++
helpviewer_keywords: C4117
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 90294dee477b93f59a6b5327406668bbc1891185
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4117"></a>C4117 kompilátoru upozornění (úroveň 1)
je vyhrazený název makro 'name'; Příkaz ignorován  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Při definování nebo nedefinované předdefinovaná makra.  
  
2.  Při definování nebo nedefinované operátor preprocesoru **definované**.  
  
 Následující ukázka generuje C4117:  
  
```  
// C4117.cpp  
// compile with: /W1  
#define __FILE__ test         // C4117. __FILE__ is a predefined macro  
#define ValidMacroName test   // ok  
  
int main() {  
}  
```