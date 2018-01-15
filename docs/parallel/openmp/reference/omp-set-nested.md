---
title: "omp_set_nested – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_set_nested
dev_langs: C++
helpviewer_keywords: omp_set_nested OpenMP function
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f08fec246b5df4b5a6dc965917e0a6438b58042f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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