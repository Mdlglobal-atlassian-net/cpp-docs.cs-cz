---
title: C3015 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3015
dev_langs:
- C++
helpviewer_keywords:
- C3015
ms.assetid: d5e8e50b-7542-4b2d-8665-1b22072a5bc6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c3599cdab1307ccff4677b823b49d94d710adfd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3015"></a>C3015 chyby kompilátoru
Inicializace v OpenMP pro příkaz má nesprávné formuláře  
  
 A `for` smyčky v příkazu OpenMP musí být plně a explicitně zadán.  
  
 Následující ukázka generuje C3015:  
  
```  
// C3015.cpp  
// compile with: /openmp  
int main()  
{  
   int i = 0, j = 10;  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      for (; i < 0; i += j)   // C3015  
      // Try the following line instead:  
      // for (i = 0; i < 0; i++)   
         --j;  
   }  
}  
```