---
title: "C3499 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3499
dev_langs:
- C++
helpviewer_keywords:
- C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 141d21be57d1aaa6957bbb9fe2d1ac5c0139076a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3499"></a>C3499 chyby kompilátoru
lambda, který byl zadaný mít typ vrácené hodnoty void nelze vrátit hodnotu  
  
 Kompilátor generuje této chybě, pokud výraz lambda, která určuje `void` jako návratový typ, vrátí hodnotu, nebo když výrazu lambda obsahuje více než jeden výraz a vrátí hodnotu, ale neurčuje její návratový typ.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nevrátí hodnotu z výrazu lambda, nebo  
  
-   Zadat návratový typ výrazu lambda, nebo  
  
-   Kombinace příkazů, které tvoří část výrazu lambda do jednoho příkazu.  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje C3499, protože text výrazu lambda obsahuje více příkazů a vrátí hodnotu, ale výrazu lambda neurčuje návratový typ:  
  
```  
// C3499a.cpp  
  
int main()  
{  
   [](int x) { int n = x * 2; return n; } (5); // C3499  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje na C3499 dvě možná řešení. Na první řešení poskytuje návratový typ výrazu lambda. Druhé řešení kombinuje příkazů, které tvoří část výrazu lambda do jednoho příkazu.  
  
```  
// C3499b.cpp  
  
int main()  
{  
   // Possible resolution 1:   
   // Provide the return type of the lambda expression.  
   [](int x) -> int { int n = x * 2; return n; } (5);  
  
   // Possible resolution 2:   
   // Combine the statements that make up the body of   
   // the lambda expression into a single statement.  
   [](int x) { return x * 2; } (5);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)