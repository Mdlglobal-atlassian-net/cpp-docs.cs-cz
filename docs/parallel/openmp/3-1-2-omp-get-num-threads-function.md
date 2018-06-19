---
title: 3.1.2 omp_get_num_threads – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df01d571b67ff6d252d85128fcc8c1d26a6e94a9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687436"
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