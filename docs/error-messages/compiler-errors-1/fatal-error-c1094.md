---
title: "Závažná chyba C1094 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1094
dev_langs:
- C++
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 630ed1979656351f6816ac5c24a7cbe386e62cce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1094"></a>Závažná chyba C1094
'-Zmval1': možnost příkazového řádku je nekonzistentní s hodnotou sloužící k vytvoření předkompilovaných hlaviček ('-Zmval2.)  
  
 Hodnota, která je předána [/Yc](../../build/reference/yc-create-precompiled-header-file.md) musí mít stejnou hodnotu, která je předána [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (**/Zm** hodnoty musí být stejná ve všech kompilací, které můžete použít nebo vytvořit stejné předkompilovaných Hlavičkový soubor).  
  
 Následující ukázka generuje C1094:  
  
```  
// C1094.h  
int func1();  
```  
  
 A pak  
  
```  
// C1094.cpp  
// compile with: /Yc"C1094.h" /Zm200  
int u;  
int main() {  
   int sd = 32;  
}  
#include "C1094.h"  
```  
  
 A pak  
  
```  
// C1094b.cpp  
// compile with: /Yu"C1094.h" /Zm300 /c  
#include "C1094.h"   // C1094 compile with /Zm200  
void Test() {}  
```