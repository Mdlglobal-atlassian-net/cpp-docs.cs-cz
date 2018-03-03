---
title: "C3483 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2ea5c703e9617bd419a3e390f143c0defd7ca9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3483"></a>C3483 chyby kompilátoru
'var' je již součástí seznamu zachycení lambda  
  
 Stejnou proměnnou byl předán zachycení seznam výrazu lambda více než jednou.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte všechny další instance proměnné ze seznamu zachycení.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří C3483, protože proměnná `n` se zobrazí v seznamu zachycení výrazu lambda více než jednou:  
  
```  
// C3483.cpp  
  
int main()  
{  
   int m = 6, n = 5;  
   [m,n,n] { return n + m; }(); // C3483  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)