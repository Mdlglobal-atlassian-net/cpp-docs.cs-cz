---
title: "C3042 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3042
dev_langs: C++
helpviewer_keywords: C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15099fd212c58df0369749a497a277ecb7f6987e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3042"></a>C3042 chyby kompilátoru
klauzule 'copyprivate' a 'nowait' se nemůže vyskytovat společně na "směrnice" OpenMP – direktiva  
  
 [Copyprivate](../../parallel/openmp/reference/copyprivate.md) a [nowait](../../parallel/openmp/reference/nowait.md) klauzule se vzájemně vylučují na zadaný direktivu. Chcete-li tuto chybu opravit, odeberte jednu nebo obě `copyprivate` nebo `nowait` klauzule.  
  
 Následující ukázka generuje C3042:  
  
```  
// C3042.cpp  
// compile with: /openmp /c  
#include <stdio.h>  
#include "omp.h"  
  
double d;  
  
int main() {  
    #pragma omp parallel private(d)  
   {  
      #pragma omp single copyprivate(d) nowait   // C3042  
      {  
      }  
   }  
}  
```