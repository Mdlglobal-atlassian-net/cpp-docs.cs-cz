---
title: "Kompilátoru (úroveň 1) upozornění C4353 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4353
dev_langs: C++
helpviewer_keywords: C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b64e2a43f6d85499c1884a9cc14e6f615f7bf8b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4353"></a>C4353 kompilátoru upozornění (úroveň 1)
nestandardní rozšíření používané: Konstanta 0 jako výraz funkce. Místo toho použijte '__noop' – vnitřní funkce  
  
 Nelze použít konstantní nula (0) jako výraz funkce. Další informace najdete v tématu [__noop](../../intrinsics/noop.md).  
  
 Následující ukázka generuje C4353:  
  
```  
// C4353.cpp  
// compile with: /W1  
void MyPrintf(void){};  
#define X 0  
#if X  
   #define DBPRINT MyPrint  
#else  
   #define DBPRINT 0   // C4353 expected  
#endif  
int main(){  
DBPRINT();  
}  
```