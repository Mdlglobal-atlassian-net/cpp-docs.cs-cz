---
title: "Kompilátoru (úroveň 1) upozornění C4549 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4549
dev_langs: C++
helpviewer_keywords: C4549
ms.assetid: 81a07676-625b-4f58-9b0c-3ee22830b04a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d05ef4857d7933efe67312e74515135f6262e8d8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4549"></a>C4549 kompilátoru upozornění (úroveň 1)
'operátor': operátor před čárkou nemá žádný vliv; hodláte 'operátor'?  
  
 Kompilátor zjištěna výraz nesprávně formátovaných čárkami.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. Další informace najdete v tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 Následující ukázka generuje C4549:  
  
```  
// C4549.cpp  
// compile with: /W1  
#pragma warning (default : 4549)  
  
int main() {  
   int i = 0, k = 0;  
  
   if ( i == 0, k )   // C4549  
   // try the following line instead  
   // if ( i == 0 )  
      i++;  
}  
```