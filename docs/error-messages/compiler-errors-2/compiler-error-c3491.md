---
title: "C3491 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3491
dev_langs:
- C++
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8c126ae0533424c19fd29ea48dbea8c3d7e8971
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3491"></a>C3491 chyby kompilátoru
'příkaz var': zachycení-hodnota nemůže být upravena v neměnitelnou lambda  
  
 Výraz lambda neměnitelnou nelze změnit hodnotu proměnné, která zachycenou hodnotu.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Deklarovat výraz lambda s `mutable` – klíčové slovo, nebo  
  
-   Předejte proměnnou s odkazem na seznamu zachycení výrazu lambda.  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje C3491, protože text výrazu lambda neměnitelnou upraví zachycená proměnná `m`:  
  
```  
// C3491a.cpp  
  
int main()  
{  
   int m = 55;  
   [m](int n) { m = n; }(99); // C3491  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad přeloží C3491 deklarováním výrazu lambda s `mutable` – klíčové slovo:  
  
```  
// C3491b.cpp  
  
int main()  
{  
   int m = 55;  
   [m](int n) mutable { m = n; }(99);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)