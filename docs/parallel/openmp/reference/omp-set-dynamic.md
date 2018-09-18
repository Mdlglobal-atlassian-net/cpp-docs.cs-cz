---
title: omp_set_dynamic – | Dokumentace Microsoftu
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
ms.openlocfilehash: c3e8ac574ce304238affbab41acc415e1d8de697
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026904"
---
# <a name="ompsetdynamic"></a>omp_set_dynamic
Označuje, že je možné upravit počet vláken v následných paralelní oblasti podle času spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_set_dynamic(  
   int val  
);  
```  
  
### <a name="parameters"></a>Parametry
  
*Val*<br/>
Hodnota označující, pokud je možné upravit počet vláken v následných paralelní oblasti modulem runtime.  Pokud nenulovou hodnotu, že modul runtime můžete upravit počet vláken, pokud je nula, modul runtime nebude dynamicky upravit počet vláken.  
  
## <a name="remarks"></a>Poznámky  
 Počet vláken se nikdy nepřekročí hodnotu nastavenou [omp_set_num_threads –](../../../parallel/openmp/reference/omp-set-num-threads.md) nebo [OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md).  
  
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