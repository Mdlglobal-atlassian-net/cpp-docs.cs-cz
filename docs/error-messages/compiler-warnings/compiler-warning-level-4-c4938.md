---
title: "Kompilátoru (úroveň 4) upozornění C4938 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4938
dev_langs:
- C++
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 102e0eeb7b682afed595be2be08c2ee8a69487f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4938"></a>C4938 kompilátoru upozornění (úroveň 4)
'příkaz var': plovoucí redukční proměnnou bod může způsobit nekonzistentní výsledky v rámci /fp: striktní nebo fenv_access – #pragma  
  
 Neměli byste používat [/fp: striktní](../../build/reference/fp-specify-floating-point-behavior.md) nebo [fenv_access –](../../preprocessor/fenv-access.md) s OpenMP s plovoucí desetinnou čárkou snížení, protože součet je vypočítán v jiném pořadí. Výsledky se proto může lišit od výsledky bez/OpenMP.  
  
 Následující ukázka generuje C4938:  
  
```  
// C4938.cpp  
// compile with: /openmp /W4 /fp:strict /c  
// #pragma fenv_access(on)  
extern double *a;   
  
double test(int first, int last) {   
   double sum = 0.0;   
   #pragma omp parallel for reduction(+: sum)   // C4938  
   for (int i = first ; i <= last ; ++i)   
      sum += a[i];   
   return sum;   
}  
```  
  
 Bez explicitní paralelizace součet vypočítán takto:  
  
```  
sum = a[first] + a[first + 1] + ... + a[last];   
```  
  
 Explicitní paralelizace (a dvěma vlákny) je součet vypočítán takto:  
  
```  
sum1 = a[first] + ... a[first + last / 2];   
sum2 = a[(first + last / 2) + 1] + ... a[last];   
sum = sum1 + sum2;  
```