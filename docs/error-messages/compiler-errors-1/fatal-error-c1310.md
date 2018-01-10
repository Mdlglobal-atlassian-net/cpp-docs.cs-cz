---
title: "Závažná chyba C1310 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1310
dev_langs: C++
helpviewer_keywords: C1310
ms.assetid: ac48aa51-8023-42fe-b844-3f8bf228fbef
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d07d0efae792a243af161989799fe9ffa59abbed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1310"></a>Závažná chyba C1310
optimalizace na základě profilu nejsou k dispozici s OpenMP  
  
 Nebudete moci propojit s [/LTCG:PGI](../../build/reference/ltcg-link-time-code-generation.md) libovolný modul, který byl kompilován s [/GL](../../build/reference/gl-whole-program-optimization.md).  
  
 Následující ukázka generuje C1310:  
  
```  
// C1310.cpp  
// compile with: /openmp /GL /link /LTCG:PGI  
// C1310 expected  
int main()  
{  
   int i = 0, j = 10;  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      for (i = 0; i < 0; i++)   
         --j;  
   }  
}  
```