---
title: paralelní | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- parallel
dev_langs:
- C++
helpviewer_keywords:
- parallel OpenMP directive
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e0436dbbc75690d38b5930a491b7058ee095341
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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
  
 `clause` (volitelné)  
 Nula nebo více klauzulích.  Najdete v části poznámky seznam klauzulích nepodporuje **paralelní**.  
  
## <a name="remarks"></a>Poznámky  
 **Paralelní** podporuje následující klauzule OpenMP – direktiva:  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [default](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [if](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
-   [Sdílené](../../../parallel/openmp/reference/shared-openmp.md)  
  
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
 [Direktivy](../../../parallel/openmp/reference/openmp-directives.md)