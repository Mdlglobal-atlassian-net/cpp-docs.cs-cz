---
title: C3480 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3480
dev_langs:
- C++
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 673eff58b09fe1f2bbfe8a7629594399e8ca6b22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3480"></a>C3480 chyby kompilátoru
'příkaz var': zachycená proměnná lambda musí být ze nadřazených oboru – funkce  
  
 Zachycená proměnná lambda není ze nadřazených oboru funkce.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Proměnná odeberte ze seznamu zachycení výrazu lambda.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří C3480, protože proměnná `global` není ze nadřazených oboru funkce:  
  
```  
// C3480a.cpp  
  
int global = 0;  
int main()  
{  
   [&global] { global = 5; }(); // C3480  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad přeloží C3480 odebráním proměnnou `global` ze seznamu zachycení výrazu lambda:  
  
```  
// C3480b.cpp  
  
int global = 0;  
int main()  
{  
   [] { global = 5; }();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)