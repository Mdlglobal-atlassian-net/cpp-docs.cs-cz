---
title: C3490 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3490
dev_langs:
- C++
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 593e5509ada926f27243a761da3470eb2d846a22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258747"
---
# <a name="compiler-error-c3490"></a>C3490 chyby kompilátoru
'příkaz var' nelze upravit, protože je přistupuje prostřednictvím const objektu  
  
 Výraz lambda, která je definována v `const` metoda nemohou upravovat data neměnitelnou člen.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte `const` modifikátor z vaší deklarace metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří C3490, protože upravuje členské proměnné `_i` v `const` metoda:  
  
```  
// C3490a.cpp  
// compile with: /c  
  
class C  
{  
   void f() const   
   {  
      auto x = [=]() { _i = 20; }; // C3490  
   }  
  
   int _i;  
};  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad přeloží C3490 odebráním `const` modifikátor z deklarace metody:  
  
```  
// C3490b.cpp  
// compile with: /c  
  
class C  
{  
   void f()  
   {  
      auto x = [=]() { _i = 20; };  
   }  
  
   int _i;  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)