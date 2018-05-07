---
title: C3491 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3491
dev_langs:
- C++
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bd856f50f3528b3895e4495215b2e479d8a424b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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