---
title: C3043 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3043
dev_langs:
- C++
helpviewer_keywords:
- C3043
ms.assetid: 0ef55e63-e82b-48eb-9d44-690950ac34c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fdbb8f3cf9a0e996bc6ace521cd2bdd8b5e5dcc8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3043"></a>C3043 chyby kompilátoru
OpenMP – direktiva 'kritické' nelze vnořit v direktivě, kritické"se stejným názvem  
  
 A [kritické](../../parallel/openmp/reference/critical.md) – direktiva nemůže být vnořena ve `critical` direktiva, která používá stejný název.  
  
 Následující ukázka generuje C3043:  
  
```  
// C3043.cpp  
// compile with: /openmp /c  
#include "omp.h"  
  
int main() {  
   int n1 = 1, n2 = 2, n3 = 3;  
  
   #pragma omp parallel  
   {  
      ++n2;  
  
      #pragma omp critical(MyTest)  
      {  
         ++n2;  
  
         #pragma omp critical(MyTest)   // C3043  
         // try the following line instead  
         // #pragma omp critical(MyTest2)  
         {  
            ++n3;  
         }  
      }  
   }  
}  
```