---
title: "Kompilátoru (úroveň 1) upozornění C4129 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4129
dev_langs: C++
helpviewer_keywords: C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1efeca1e597af8e7f96b2854fcbcfc49b000009a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4129"></a>C4129 kompilátoru upozornění (úroveň 1)
'znak': nerozpoznaný znak – řídicí sekvence  
  
 `character` Následující zpětné lomítko (\\) v znak nebo řetězec konstanta není rozpoznán jako platná řídicí sekvence. Zpětné lomítko bude ignorován a ne k tisku. Je vytištěno znak následující zpětné lomítko.  
  
 Pokud chcete vytisknout jedno zpětné lomítko, zadejte dvojité zpětné lomítko (\\\\).  
  
 Standard C++ v části 2.13.2 popisuje řídicí sekvence.  
  
 Následující ukázka generuje C4129:  
  
```  
// C4129.cpp  
// compile with: /W1  
int main() {  
   char array1[] = "\/709";   // C4129  
   char array2[] = "\n709";   // OK  
}  
```