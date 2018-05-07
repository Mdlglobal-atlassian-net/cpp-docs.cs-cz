---
title: Kompilátoru (úroveň 1) upozornění C4399 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b39f4919dd736e4bf2e6230fe68ea69c2b14766e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4399"></a>C4399 kompilátoru upozornění (úroveň 1)
'symbol': symbol na proces by neměl být označené jako deklarace __declspec(dllimport), když kompilujete s/clr: pure  
  
 **/CLR: pure** – možnost kompilátoru je zastaralá ve Visual Studiu 2015.  
  
 Data z nativní bitové kopie nebo bitové kopie pomocí nativní a konstrukce CLR nelze importovat do čisté bitové kopii. Toto upozornění vyřešíte kompilovat s **/CLR** (není **/CLR: pure**) nebo odstranění `__declspec(dllimport)`.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4399.  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```