---
title: "Kompilátoru (úroveň 1) upozornění C4722 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4722
dev_langs: C++
helpviewer_keywords: C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8616fe9834b0f73445bbcb8ffea4d35af3895b12
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4722"></a>C4722 kompilátoru upozornění (úroveň 1)
'function': destruktor nikdy vrátí, potenciální nevracení paměti  
  
 Tok řízení ukončí v destruktoru. Vlákno nebo celý program se ukončí a nemusí být vydán přidělené prostředky.  Kromě toho pokud destruktor bude zavolána pro uvolnění zásobníku během zpracování výjimek, chování spustitelný soubor není definován.  
  
 Chcete-li vyřešit, odeberte volání funkce, které způsobí, že destruktor není vrátit.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4722:  
  
```  
// C4722.cpp  
// compile with: /O1 /W1 /c  
#include <stdlib.h>  
class C {  
public:  
   C();  
   ~C() { exit(1); };   // C4722  
};  
  
extern void func (C*);  
  
void Test(){  
   C x;  
   func(&x);  
   // control will not leave Test because destructor will exit  
}  
```