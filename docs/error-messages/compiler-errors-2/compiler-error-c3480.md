---
title: "C3480 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3480
dev_langs: C++
helpviewer_keywords: C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 344e76f5d146e6bc715619bce7e68c80ffda211f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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