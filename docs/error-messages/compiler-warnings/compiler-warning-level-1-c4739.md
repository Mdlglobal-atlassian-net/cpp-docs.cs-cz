---
title: "Kompilátoru (úroveň 1) upozornění C4739 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4739
dev_langs: C++
helpviewer_keywords: C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a5e4184ced9a77fa389ad0909923bc8b26a3b930
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4739"></a>C4739 kompilátoru upozornění (úroveň 1)
odkaz na proměnnou 'var' překračuje jeho prostorem úložiště  
  
 Hodnota je přiřazený k proměnné, ale hodnota je větší než velikost proměnné. Paměť se zapíšou mimo umístění v paměti proměnné a ztrátě dat.  
  
 Chcete-li vyřešit toto upozornění, přiřadíte jenom hodnotu do proměnné, jejíž aktuální velikost zvládne hodnota.  
  
 Následující ukázka generuje C4739:  
  
```  
// C4739.cpp  
// compile with: /RTCs /Zi /W1 /c  
char *pc;  
int main() {  
   char c;  
   *(int *)&c = 1;   // C4739  
  
   // OK  
   *(char *)&c = 1;  
}  
```