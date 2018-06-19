---
title: C3042 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3042
dev_langs:
- C++
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32d2f88702bb3c1c2439dd2931ee269c9c1413ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250202"
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