---
title: C3495 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3495
dev_langs:
- C++
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7accbc422256abbd75d518acce72c522fbb67c14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253659"
---
# <a name="compiler-error-c3495"></a>C3495 chyby kompilátoru
'příkaz var': zachycení lambda musí mít trvání automatické uložení  
  
 Nemůže zaznamenat proměnnou, která nemá trvání automatické úložiště, například proměnná, která je označena `static` nebo `extern`.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nepředávejte `static` nebo `extern` proměnné do seznamu zachycení výrazu lambda.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří C3495, protože `static` proměnná `n` se zobrazí v seznamu zachycení výrazu lambda:  
  
```  
// C3495.cpp  
  
int main()  
{  
   static int n = 66;  
   [&n]() { return n; }(); // C3495  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)   


