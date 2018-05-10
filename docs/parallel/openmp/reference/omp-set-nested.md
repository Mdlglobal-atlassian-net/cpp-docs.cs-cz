---
title: omp_set_nested – | Microsoft Docs
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
ms.openlocfilehash: b6539167b936efdc4c9f407cd951c9c582b0a138
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ompsetnested"></a>omp_set_nested
Vnořené paralelismus umožňuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `val`  
 Pokud nenulové hodnoty, umožňuje vnořené stupně paralelního zpracování. Pokud nula, zakáže vnořené stupně paralelního zpracování.  
  
## <a name="remarks"></a>Poznámky  
 Omp – vnořené paralelismus lze zapnout s `omp_set_nested`, nebo nastavením [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md) proměnné prostředí.  
  
 Nastavení pro `omp_set_nested` přepíše nastavení jazyka `OMP_NESTED` proměnné prostředí.  
  
 Když je povolené, proměnné prostředí může dojít k narušení jinak provozní program vzhledem k tomu, že počet vláken, zvyšuje exponenciálnímu při vnoření paralelní oblasti.  Například funkce, recurses 6krát s počet vláken omp – nastavte na 4 vyžaduje 4 096 (4 exponentem 6) vláken obecně, způsobí snížení výkonu aplikace, pokud počet vláken překročí maximální počet procesorů. Jedinou výjimkou můžou být že vázána vstupně-výstupních operací aplikace.  
  
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