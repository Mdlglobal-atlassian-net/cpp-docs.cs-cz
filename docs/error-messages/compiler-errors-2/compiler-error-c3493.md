---
title: C3493 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3493
dev_langs:
- C++
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3aec62bfff59396ec73141746193e4e3f16d84fa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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