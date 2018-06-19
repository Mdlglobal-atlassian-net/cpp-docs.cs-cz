---
title: C3047 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3047
dev_langs:
- C++
helpviewer_keywords:
- C3047
ms.assetid: 91c14566-5958-433d-8549-0e8bc3196f76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4ab5f13a898d3f1c200e493d386fb59727e022c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246124"
---
# <a name="compiler-error-c3047"></a>C3047 chyby kompilátoru
Strukturované blok v OpenMP oblast 'částech' musí předcházet '#pragma omp – část.  
  
 Žádný kód v bloku kódu zaváděné [části](../../parallel/openmp/reference/sections-openmp.md) – direktiva musí být v bloku kódu zaváděné `section` – direktiva.  
  
 Následující ukázka generuje C3047:  
  
```  
// C3047.cpp  
// compile with: /openmp /c  
#include "omp.h"  
  
int main() {  
   int n2 = 2, n3 = 3;  
  
   #pragma omp parallel  
   {  
      ++n2;  
  
      #pragma omp sections  
      {  
  
         #pragma omp section  
         {  
            ++n3;  
         }  
  
         ++n2;   // C3047 not enclosed in #pragma omp section  
      }  
   }  
}  
```