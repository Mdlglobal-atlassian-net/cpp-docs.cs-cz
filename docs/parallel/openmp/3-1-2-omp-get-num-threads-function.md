---
title: "3.1.2 omp_get_num_threads – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d595fd47b87bbc3fd7701fc847821c73169a23e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="312-ompgetnumthreads-function"></a>3.1.2 omp_get_num_threads – funkce
**Omp_get_num_threads –** funkce vrátí počet vláken aktuálně v týmu provádění paralelní oblast, ve kterém je volána. Formát vypadá takto:  
  
```  
#include <omp.h>  
int omp_get_num_threads(void);  
```  
  
 **Num_threads** klauzuli **omp_set_num_threads –** funkce a **OMP_NUM_THREADS** proměnné prostředí se řídí počet vláken v týmu.  
  
 Pokud uživatel není explicitně nastavena počet vláken, výchozí hodnota je definované implementací. Tato funkce se váže k nejbližší obklopuje **paralelní** – direktiva. Pokud je volána z sériové část programu, nebo z vnořené paralelní oblasti, která je serializováno, funkce vrátí hodnotu 1.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **OMP_NUM_THREADS** proměnné, naleznete v prostředí [části 4.2](../../parallel/openmp/4-2-omp-num-threads.md) na stránce 48.  
  
-   **num_threads** klauzule, najdete v části [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.  
  
-   **paralelní** vytvořit najdete v tématu [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.