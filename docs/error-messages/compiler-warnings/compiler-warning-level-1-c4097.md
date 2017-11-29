---
title: "Kompilátoru (úroveň 1) upozornění C4097 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4097
dev_langs: C++
helpviewer_keywords: C4097
ms.assetid: 2525be51-fac2-43b2-b57c-3bbf1a2268f7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3ca91f0a8df6a78b11baf77940b1c4b21e258d23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4097"></a>C4097 kompilátoru upozornění (úroveň 1)
Parametr – Direktiva pragma jako "obnovení" nebo "vypnuto"  
  
 Pragma byla předána neplatná hodnota.  
  
 Následující ukázka generuje C4097:  
  
```  
// C4097.cpp  
// compile with: /W1  
#pragma runtime_checks("",test)   // C4097  
// try the following line instead  
// #pragma runtime_checks("",off)  
  
int main() {  
}  
```