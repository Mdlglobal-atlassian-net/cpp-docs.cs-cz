---
title: C3481 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3481
dev_langs:
- C++
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77fc0f542a74cb077e59882e31dd1acb10c7b7e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3481"></a>C3481 chyby kompilátoru
'příkaz var': lambda zachycená proměnná nebyla nalezena  
  
 Kompilátor nelze nalézt definici proměnné, která předaný zachycení seznam výrazu lambda.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Proměnná odeberte ze seznamu zachycení výrazu lambda.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří C3481, protože proměnná `n` není definován:  
  
```  
// C3481.cpp  
  
int main()  
{  
   [n] {}(); // C3481  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)