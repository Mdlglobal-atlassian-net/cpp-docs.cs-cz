---
title: "C3018 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3018
dev_langs: C++
helpviewer_keywords: C3018
ms.assetid: 685be45f-f116-43a8-a88d-05ab6616e2f1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 05d0cc8f381335b22a53a4cc699172cd289126a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3018"></a>C3018 chyby kompilátoru
'var1': OpenMP pro testovací nebo přírůstek musí používat index proměnné 'var2.  
  
 A `for` smyčky v příkazu OpenMP musí pro jeho test a přírůstek používaly stejnou proměnnou, protože využívá pro její index.  
  
 Následující ukázka generuje C3018:  
  
```  
// C3018.cpp  
// compile with: /openmp  
int main()  
{  
   int i = 0, j = 5;  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      for (i = 0; j < 10; ++i)   // C3018  
      // try the the following line instead  
      // for (i = 0; i < 10; ++i)  
         j *= 2;  
  
      #pragma omp for  
      for (i = 0; i < 10; j = j + i)   // C3018  
      // try the the following line instead  
      // for (i = 0; i < 10; i = j + i)  
         j *= 2;  
   }  
}  
```