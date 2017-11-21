---
title: "Chyba kompilátoru C3487 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3487
dev_langs: C++
helpviewer_keywords: C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eb659f2d7971d1dd2ff27c438839336d4744767e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3487"></a>Chyba kompilátoru C3487
'return typu': všechny vrátit výrazy musí odvodit do stejného typu: dříve bylo "návratový typ"  
  
 Lambda musíte zadat její návratový typ, pokud obsahuje jeden příkaz return. Pokud lambda obsahuje více příkazech return, musí všechny mají stejného typu.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zadejte koncové návratový typ pro argument lambda. Ověřte, zda všechny vrátí z argument lambda jsou stejného typu nebo může být implicitně převedena na návratový typ.  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje C3487, protože argument lambda návratové typy se neshodují:  
  
```  
// C3487.cpp  
// Compile by using: cl /c /W4 C3487.cpp  
  
int* test(int* pi) {  
   // To fix the error, uncomment the trailing return type below  
   auto odd_pointer = [=]() /* -> int* */ {  
      if (*pi % 2)   
         return pi;  
      return nullptr; // C3487 - nullptr is not an int* type  
   };  
   return odd_pointer();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)