---
title: paralelní | Dokumentace Microsoftu
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
ms.openlocfilehash: 1c8b1466eae343b6c644b6ecfbd919c3241259bf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705962"
---
# <a name="parallel"></a>parallel
Definuje paralelní oblasti, což je kód, který spustí paralelně několik vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp parallel [clauses]  
{  
   code_block  
}  
```  
  
## <a name="arguments"></a>Arguments

*Klauzule*<br/>
(Volitelné) Nula nebo více klauzulí.  Naleznete v části poznámky pro seznam klauzule podporované službou **paralelní**.  
  
## <a name="remarks"></a>Poznámky  
 **Paralelní** podporuje následující klauzule OpenMP – direktiva:  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [default](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [if](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
-   [Sdílet](../../../parallel/openmp/reference/shared-openmp.md)  
  
 **paralelní** je také možné se [oddíly](../../../parallel/openmp/reference/sections-openmp.md) a [pro](../../../parallel/openmp/reference/for-openmp.md) direktivy.  
  
 Další informace najdete v tématu [2.3 parallel – konstrukce](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit počet vláken a definovat paralelní oblasti. Ve výchozím nastavení počet vláken je rovna počtu logických procesorů v počítači. Například pokud máte počítače s jednoho fyzického procesoru, s povoleným hyperthreadingem, bude mít dva logické procesory a proto se dvěma vlákny.  
  
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
 Všimněte si, že pořadí výstup se může lišit na různých strojích.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy](../../../parallel/openmp/reference/openmp-directives.md)