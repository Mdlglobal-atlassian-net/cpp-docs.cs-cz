---
title: "C3020 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3020
dev_langs: C++
helpviewer_keywords: C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4da505740eba9b291d8c4139cf9cd6fded70fdfa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3020"></a>C3020 chyby kompilátoru
'příkaz var': index proměnná OpenMP smyčka for nemůže být upraven do těla smyčky  
  
 OpenMP `for` smyčky nesmí změnit index (smyčky čítač) v textu `for` smyčky.  
  
 Následující ukázka generuje C3020:  
  
```  
// C3020.cpp  
// compile with: /openmp  
int main() {  
   int i = 0, n = 3;  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      for (i = 0; i < 10; i += n)  
         i *= 2;   // C3020  
         // try the following line instead  
         // n++;  
   }  
}  
```  
  
 Proměnná definovaná s [lastprivate](../../parallel/openmp/reference/lastprivate.md) nelze použít jako index uvnitř parallelized smyčky.  
  
 Následující ukázka získáte C3020 pro druhý lastprivate vzhledem k tomu, že lastprivate aktivují zápisu do idx_a v rámci krajních pro smyčky. První lastprivate nedává k chybě, protože tento lastprivate aktivuje zápisu do idx_a mimo krajních pro smyčky (technicky na konci velmi poslední iteraci). Následující ukázka generuje C3020.  
  
```  
// C3020b.cpp  
// compile with: /openmp /c  
float a[100][100];  
int idx_a, idx_b;  
void test(int first, int last)  
{  
   #pragma omp parallel for lastprivate(idx_a)  
   for (idx_a = first; idx_a <= last; ++idx_a) {  
      #pragma omp parallel for lastprivate(idx_a)   // C3020  
      for (idx_b = first; idx_b <= last; ++idx_b) {  
         a[idx_a][idx_b] += 1.0f;  
      }  
   }  
}  
```  
  
 Následující příklad ukazuje možná řešení:  
  
```  
// C3020c.cpp  
// compile with: /openmp /c  
float a[100][100];  
int idx_a, idx_b;  
void test(int first, int last)  
{  
   #pragma omp parallel for lastprivate(idx_a)  
   for (idx_a = first; idx_a <= last; ++idx_a) {  
      #pragma omp parallel for lastprivate(idx_b)  
      for (idx_b = first; idx_b <= last; ++idx_b) {  
         a[idx_a][idx_b] += 1.0f;  
      }  
   }  
}  
```