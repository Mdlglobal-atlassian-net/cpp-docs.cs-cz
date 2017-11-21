---
title: "C3490 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3490
dev_langs: C++
helpviewer_keywords: C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 42923edc2d238e7f0b64858561f7d23d211abd80
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)