---
title: "Kompilátoru (úroveň 4) upozornění C4208 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4208
dev_langs: C++
helpviewer_keywords: C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f6ccd7d9590149f9391791ae6d290b165e6ce254
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4208"></a>C4208 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: odstranění [exp] - exp vyhodnocen ale ignorovat  
  
 Pomocí rozšíření Microsoft (/Ze), můžete odstranit pomocí hodnoty v závorkách s pole [delete – operátor](../../cpp/delete-operator-cpp.md). Hodnota se ignoruje.  
  
```  
// C4208.cpp  
// compile with: /W4  
int main()  
{  
   int * MyArray = new int[18];  
   delete [18] MyArray;      // C4208  
   MyArray = new int[18];  
   delete [] MyArray;        // ok  
}  
```  
  
 Tyto hodnoty jsou neplatné v části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).