---
title: "paralelní | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: parallel
dev_langs: C++
helpviewer_keywords: parallel OpenMP directive
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 289a4928c9c46f6d758ddc2f30ed864488ab725e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="parallel"></a>parallel
Definuje paralelní oblasti, která je kód, který budou spuštěny několik vláken současně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp parallel [clauses]  
{  
   code_block  
}  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `clause`(volitelné)  
 Nula nebo více klauzulích.  Najdete v části poznámky seznam klauzulích nepodporuje **paralelní**.  
  
## <a name="remarks"></a>Poznámky  
 **Paralelní** podporuje následující klauzule OpenMP – direktiva:  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [Výchozí](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [Pokud](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [privátní](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [snížení](../../../parallel/openmp/reference/reduction.md)  
  
-   [sdílené](../../../parallel/openmp/reference/shared-openmp.md)  
  
 **paralelní** lze také použít s [části](../../../parallel/openmp/reference/sections-openmp.md) a [pro](../../../parallel/openmp/reference/for-openmp.md) direktivy.  
  
 Další informace najdete v tématu [2.3 parallel – konstrukce](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit počet vláken a definovat paralelní oblast. Ve výchozím nastavení počet vláken, se rovná počet logických procesorů na počítači. Například pokud máte počítač s jednoho fyzického procesoru, který má povoleným Hyper-threadingem, bude mít dva logické procesory a tedy dvě vláken.  
  
```  
// omp_parallel.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(4)  
   {  
      int i = omp_get_thread_num();  
      printf_s("Hello from thread %d\n", i);  
   }  
}  
```  
  
```Output  
Hello from thread 0  
Hello from thread 1  
Hello from thread 2  
Hello from thread 3  
```  
  
## <a name="comment"></a>Komentář  
 Všimněte si, že pořadí výstupu se může lišit na různé počítače.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy jazyka](../../../parallel/openmp/reference/openmp-directives.md)