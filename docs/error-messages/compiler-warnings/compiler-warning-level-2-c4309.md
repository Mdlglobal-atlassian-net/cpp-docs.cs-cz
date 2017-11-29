---
title: "Kompilátoru (úroveň 2) upozornění C4309 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4309
dev_langs: C++
helpviewer_keywords: C4309
ms.assetid: cb3f41ef-fd8a-4def-baa1-924e751fca68
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 43d4da7be0fa4e37cb87524b8e165800f21d1855
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-2-c4309"></a>C4309 kompilátoru upozornění (úroveň 2)
'Převod': zkrácení konstantní hodnoty  
  
 Převod typu způsobí, že konstanta delší než místo pro něj přidělené. Musíte používat typ, který větší pro konstantu.  
  
 Následující ukázka generuje C4309:  
  
```  
// C4309.cpp  
// compile with: /W2  
int main()  
{  
   char c = 128;   // C4309  
}  
```