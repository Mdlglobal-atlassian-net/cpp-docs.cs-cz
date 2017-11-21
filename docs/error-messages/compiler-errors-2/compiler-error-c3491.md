---
title: "C3491 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3491
dev_langs: C++
helpviewer_keywords: C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 58458a1ab0b67eb4fa6d38d0be2fb38f6d7496eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)