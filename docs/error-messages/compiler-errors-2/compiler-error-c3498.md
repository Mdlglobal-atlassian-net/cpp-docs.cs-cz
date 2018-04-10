---
title: C3498 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C3498
dev_langs:
- C++
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d895c0dc40d94d6a8fcd567173e2d596e68e333
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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