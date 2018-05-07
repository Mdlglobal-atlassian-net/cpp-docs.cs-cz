---
title: C3498 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3498
dev_langs:
- C++
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 913caa8fc73e5fe325a9d17a48b6c2b9ba641546
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3498"></a>C3498 chyby kompilátoru
'příkaz var': nemůže zaznamenat proměnnou, která má spravované nebo WinRTtype  
  
 Nemůže zaznamenat proměnnou, která obsahuje spravovaný typ nebo typ prostředí Windows Runtime v lambda.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Předat spravovaný nebo proměnná prostředí Windows Runtime do seznamu parametrů výrazu lambda.  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje C3498, protože proměnné, která obsahuje spravovaný typ se zobrazí v seznamu zachycení výrazu lambda:  
  
```  
// C3498a.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [&s](String ^ r)   
      { return String::Concat(s, r); } (", World!"); // C3498  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad přeloží C3498 předáním proměnnou spravované `s` do seznamu parametrů výrazu lambda:  
  
```  
// C3498b.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [](String ^ s, String ^ r)   
      { return String::Concat(s, r); } (s, ", World!");  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)