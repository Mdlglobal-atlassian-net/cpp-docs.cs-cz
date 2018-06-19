---
title: C3483 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e2605674ff701f70f7be6ea1b4158c9f8f0c6ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258734"
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