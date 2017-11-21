---
title: "C3039 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3039
dev_langs: C++
helpviewer_keywords: C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f3162ab8241781cda521fa4fc9dc51f14fa42897
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3039"></a>C3039 chyby kompilátoru
'příkaz var': index proměnné v OpenMP pro příkaz nemůže být redukční proměnnou  
  
 Proměnná index je implicitně privátní, takže proměnnou nelze použít v [snížení](../../parallel/openmp/reference/reduction.md) klauzuli v uzavření [paralelní](../../parallel/openmp/reference/parallel.md) – direktiva.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3039:  
  
```  
// C3039.cpp  
// compile with: /openmp /c  
int g_i;  
  
int main() {  
   int i;  
  
   #pragma omp parallel reduction(+: i)  
   {  
      #pragma omp for  
      for (i = 0; i < 10; ++i)   // C3039  
         g_i += i;  
   }  
}  
```