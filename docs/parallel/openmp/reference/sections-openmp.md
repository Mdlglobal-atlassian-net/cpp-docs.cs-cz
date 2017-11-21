---
title: "oddíly (OpenMP) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- section
- SECTIONS
dev_langs: C++
helpviewer_keywords: sections OpenMP directive
ms.assetid: 4cd1d776-e198-470e-930a-01fb0ab0a0bd
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3dbe6474b8fa957c07c334641e0e95cdc5b07878
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sections-openmp"></a>sections (OpenMP)
Určuje kód oddíly pro rozdělí mezi všechna vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp [parallel] sections [clauses]  
{  
   #pragma omp section  
   {  
      code_block   
   }   
}  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `clause`(volitelné)  
 Nula nebo více klauzulích. Najdete v části poznámky seznam klauzulích nepodporuje **části**.  
  
## <a name="remarks"></a>Poznámky  
 **Části** – direktiva může obsahovat nula nebo více **části** direktivy.  
  
 **Části** podporuje následující klauzule OpenMP – direktiva:  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [privátní](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [snížení](../../../parallel/openmp/reference/reduction.md)  
  
 Pokud **paralelní** rovněž je zadán, `clause` může všechny klauzule přijmout **paralelní** nebo **části** direktivy, s výjimkou `nowait`.  
  
 Další informace najdete v tématu [2.4.2 sections – konstrukce](../../../parallel/openmp/2-4-2-sections-construct.md).  
  
## <a name="example"></a>Příklad  
  
```  
// omp_sections.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
    #pragma omp parallel sections num_threads(4)  
    {  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
        #pragma omp section  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
    }  
}  
```  
  
```Output  
Hello from thread 0  
Hello from thread 0  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy jazyka](../../../parallel/openmp/reference/openmp-directives.md)