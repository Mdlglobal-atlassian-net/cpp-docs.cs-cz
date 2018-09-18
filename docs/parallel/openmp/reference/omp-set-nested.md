---
title: omp_set_nested – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nested OpenMP function
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc3506c35dca469febafe21509064abc1726d633
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116879"
---
# <a name="ompsetnested"></a>omp_set_nested
Povolí vnořená paralelismu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
### <a name="parameters"></a>Parametry
  
*Val*<br/>
Nenulovou hodnotu, pokud se povolí vnořená paralelismu. Pokud je nula, zakáže vnořené paralelismu.  
  
## <a name="remarks"></a>Poznámky  
 OMP vnořené paralelismu, lze zapnout pomocí `omp_set_nested`, nebo nastavením [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md) proměnné prostředí.  
  
 Nastavení pro `omp_set_nested` přepíše nastavení jazyka `OMP_NESTED` proměnné prostředí.  
  
 Pokud povolená, proměnné prostředí můžete přerušit jinak provozní program vzhledem k tomu, že počet vláken zvyšuje exponenciálně při vnoření paralelních oblastí.  Například funkce, vyžaduje recurses 6krát s počtem vláken OMP nastavena na 4 4 096 (4 k elektrické energie 6) vlákna obecně platí, způsobí snížení výkonu aplikace, pokud číslo vlákna překročí počet procesorů. Jedinou výjimkou by být že vázaný vstupně-výstupních operací aplikace.  
  
 Použití [omp_get_nested –](../../../parallel/openmp/reference/omp-get-nested.md) zobrazíte aktuální nastavení `omp_set_nested`.  
  
 Další informace najdete v tématu [3.1.9 omp_set_nested – funkce](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).  
  
## <a name="example"></a>Příklad  
  
```  
// omp_set_nested.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    omp_set_nested(1);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_nested( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_nested( ));  
        }  
}  
```  
  
```Output  
1  
1  
```  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)