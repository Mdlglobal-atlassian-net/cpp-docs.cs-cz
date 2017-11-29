---
title: "Kompilátoru (úroveň 1) upozornění C4155 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4155
dev_langs: C++
helpviewer_keywords: C4155
ms.assetid: ba233353-09e3-4195-8127-13a27ddd8d70
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 76e709491c221d7fba9516b8d005c5455921eaa7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4155"></a>C4155 kompilátoru upozornění (úroveň 1)
Odstranění pole výraz bez použití pole formuláře, odstranit.  
  
 Pole tvaru **odstranit** se má použít k odstranění pole. Toto upozornění se zobrazí pouze v rámci kompatibility ANSI (/Za).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4155:  
  
```  
// C4155.cpp  
// compile with: /Za /W1  
#include <stdio.h>  
  
int main(void)  
{  
    int (*array)[ 10 ] = new int[ 5 ] [ 10 ];  
    array[0][0] = 8;  
  
    printf_s("%d\n", array[0][0]);  
  
   delete array;   // C4155  
    // try the following line instead  
    // delete [] array;   // C4155  
}  
```