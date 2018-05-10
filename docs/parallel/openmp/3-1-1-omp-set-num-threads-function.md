---
title: 3.1.1 omp_set_num_threads – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99c82ff324cbf21612d2459511877d152e2757f5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads – funkce
`omp_set_num_threads` Funkce nastaví výchozí počet vláken používaných pro následné paralelní oblasti, které neurčují `num_threads` klauzule. Formát vypadá takto:  
  
```  
#include <omp.h>  
void omp_set_num_threads(int num_threads);  
```  
  
 Hodnota parametru *num_threads* musí být kladné celé číslo. Jeho dopad závisí na tom, jestli je dynamické přizpůsobení počet vláken, povolena. Pro komplexní sadu pravidel o interakci mezi `omp_set_num_threads` funkce a dynamické přizpůsobení vláken, najdete v části 2.3 na stránce 8.  
  
 Tato funkce má důsledky popsané výše při volání z části program kde `omp_in_parallel` funkce vrátí hodnotu 0. Pokud je volána z část programu kde `omp_in_parallel` funkce vrátí nenulovou hodnotu, chování tato funkce není definován.  
  
 Toto volání má vyšší prioritu než `OMP_NUM_THREADS` proměnné prostředí. Výchozí hodnota pro počet vláken, které lze stanovit voláním `omp_set_num_threads` nebo nastavením `OMP_NUM_THREADS` proměnné prostředí, může být explicitně přepsáno na jednom **paralelní** direktivy zadáním `num_threads` klauzule.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   `omp_set_dynamic` Funkce, najdete v části [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.  
  
-   `omp_get_dynamic` Funkce, najdete v části [části 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) na stránce 40.  
  
-   `OMP_NUM_THREADS` proměnné, naleznete v prostředí [části 4.2](../../parallel/openmp/4-2-omp-num-threads.md) na stránce 48 a 2.3 části na stránce 8.  
  
-   `num_threads` klauzule, najdete v části [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8