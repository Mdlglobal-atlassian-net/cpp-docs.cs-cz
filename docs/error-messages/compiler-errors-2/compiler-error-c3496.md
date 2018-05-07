---
title: C3496 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3496
dev_langs:
- C++
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbc128c1e9a80c61ad42514827bbf8d47b693e84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3496"></a>C3496 chyby kompilátoru
hodnota vždy zachycenou 'this': 'a' ignorovat  
  
 Nelze zaznamenat `this` ukazatel odkazem.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zaznamenat `this` ukazatel hodnotou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří C3496, protože odkaz na `this` ukazatel se zobrazí v seznamu zachycení výrazu lambda:  
  
```  
// C3496.cpp  
// compile with: /c  
  
class C  
{  
   void f()  
   {  
      [&this] {}(); // C3496  
   }  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)