---
title: "Kompilátoru (úroveň 1) upozornění C4399 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eff01c29d423b0823b41bf63702cf42ee839a523
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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