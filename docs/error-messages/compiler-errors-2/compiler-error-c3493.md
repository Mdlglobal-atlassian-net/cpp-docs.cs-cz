---
title: "C3493 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3493
dev_langs:
- C++
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8094b3b03f06dcc799b6bdfeea2b57399f92b852
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3493"></a>C3493 chyby kompilátoru
'příkaz var' nelze implicitně zaznamenat, protože nebyl zadán žádný výchozí režim zachytávání  
  
 Zachytávání výrazu lambda prázdný, `[]`, určuje výraz lambda nebude explicitně nebo implicitně zaznamenat žádné proměnné.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zadejte výchozí režim zachycení, nebo  
  
-   Explicitně zachytit jednu nebo více proměnných.  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje C3493, protože upravuje externí proměnné, ale určuje klauzuli prázdný zachycení:  
  
```  
// C3493a.cpp  
  
int main()  
{  
   int m = 55;  
   [](int n) { m = n; }(99); // C3493  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad přeloží C3493 zadáním odkazem jako výchozí režim zachytávání.  
  
```  
// C3493b.cpp  
  
int main()  
{  
   int m = 55;  
   [&](int n) { m = n; }(99);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)