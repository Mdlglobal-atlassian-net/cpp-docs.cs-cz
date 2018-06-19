---
title: Chyba kompilátoru C3487 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3487
dev_langs:
- C++
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb30b9a2cb0b77eff0888da6c387bd3b06182721
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256334"
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
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)