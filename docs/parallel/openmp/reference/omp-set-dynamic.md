---
title: omp_set_dynamic – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_set_dynamic OpenMP function
ms.assetid: 3845faf2-a0ca-45a5-ae70-2a7a6164f1e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18521113125eb49fa413568b6a62472bb50a7924
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ompsetdynamic"></a>omp_set_dynamic
Označuje, že počet vláken, která je k dispozici v dalších paralelní oblasti lze upravit podle času spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_set_dynamic(  
   int val  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `val`  
 Hodnota, která označuje, pokud lze upravit počet vláken, která je k dispozici v dalších paralelní oblasti modulem runtime.  Pokud nenulové, že modul runtime, můžete upravit počet vláken, pokud nula, nebude modul runtime dynamicky upravit počet vláken.  
  
## <a name="remarks"></a>Poznámky  
 Počet vláken, se nikdy překročit hodnotu, která nastavuje [omp_set_num_threads –](../../../parallel/openmp/reference/omp-set-num-threads.md) nebo [OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md).  
  
 Použití [omp_get_dynamic –](../../../parallel/openmp/reference/omp-get-dynamic.md) zobrazíte aktuální nastavení `omp_set_dynamic`.  
  
 Nastavení pro `omp_set_dynamic` přepíše nastavení jazyka [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md) proměnné prostředí.  
  
 Další informace najdete v tématu [3.1.7 omp_set_dynamic – funkce](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).  
  
## <a name="example"></a>Příklad  
  
```  
// omp_set_dynamic.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main()   
{  
    omp_set_dynamic(9);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_dynamic( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_dynamic( ));  
        }  
}  
```  
  
```Output  
1  
1  
```  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)