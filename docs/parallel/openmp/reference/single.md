---
title: jeden | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Single
dev_langs: C++
helpviewer_keywords: single OpenMP directive
ms.assetid: 85cf94fb-cb9c-4d82-8609-adffa9f552e1
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 898a175963698d1f44f90f08c21015a765892017
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="single"></a>single
Umožňuje určit, zda se má provést části kódu, na jedno vlákno, nikoli nutně hlavní vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp single [clauses]   
{  
   code_block   
}  
```  
  
#### <a name="parameters"></a>Parametry  
 `clause`(volitelné)  
 Nula nebo více klauzulích. Najdete v části poznámky seznam klauzulích nepodporuje **jeden**.  
  
## <a name="remarks"></a>Poznámky  
 **Jeden** podporuje následující klauzule OpenMP – direktiva:  
  
-   [copyprivate](../../../parallel/openmp/reference/copyprivate.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [privátní](../../../parallel/openmp/reference/private-openmp.md)  
  
 [Hlavní](../../../parallel/openmp/reference/master.md) umožňuje zadat, že části kódu, se má provést pouze v hlavní vlákno.  
  
 Další informace najdete v tématu [2.4.3 jeden vytvořit](../../../parallel/openmp/2-4-3-single-construct.md).  
  
## <a name="example"></a>Příklad  
  
```  
// omp_single.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(2)  
   {  
      #pragma omp single  
      // Only a single thread can read the input.  
      printf_s("read input\n");  
  
      // Multiple threads in the team compute the results.  
      printf_s("compute results\n");  
  
      #pragma omp single  
      // Only a single thread can write the output.  
      printf_s("write output\n");  
    }  
}  
```  
  
```Output  
read input  
compute results  
compute results  
write output  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy jazyka](../../../parallel/openmp/reference/openmp-directives.md)