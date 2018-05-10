---
title: 3.1.7 omp_set_dynamic – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d1e22a1eb9aff32bfaf07350daf1cb397e18eb3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic – funkce
**Omp_set_dynamic –** funkce povolí nebo zakáže dynamické přizpůsobení počet vláken, které jsou k dispozici pro spouštění paralelní oblastí. Formát vypadá takto:  
  
```  
#include <omp.h>  
void omp_set_dynamic(int dynamic_threads);  
```  
  
 Pokud *dynamic_threads* vyhodnotí nenulovou hodnotu, počet vláken, které se používají pro provádění následných paralelní oblastech mohou být upravena automaticky běhové prostředí nejlépe využívat systémové prostředky. Počet vláken, které uživatel v důsledku toho je počet maximální vláken. Počet vláken v týmu provádění paralelní oblast zůstává pevná po dobu trvání této paralelní oblasti a je hlášen **omp_get_num_threads –** funkce.  
  
 Pokud *dynamic_threads* vyhodnotí na hodnotu 0, dynamické přizpůsobení vypnutá.  
  
 Tato funkce má důsledky popsané výše při volání z části program kde **omp_in_parallel –** funkce vrátí hodnotu 0. Pokud je volána z část programu kde **omp_in_parallel –** funkce vrátí nenulovou hodnotu, chování tato funkce není definován.  
  
 Volání **omp_set_dynamic –** má vyšší prioritu než **OMP_DYNAMIC** proměnné prostředí.  
  
 Výchozí hodnota pro dynamické přizpůsobení vláken je definované implementací. V důsledku toho uživatel kódy, které závisí na konkrétní počet vláken pro správné spuštění měli explicitně zakázat dynamické vláken. Implementace nejsou potřeba umožňují dynamicky upravit počet vláken, ale jejich jsou nutné k zajištění rozhraní za účelem podpory přenositelnost pro všechny platformy.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **omp_get_num_threads –** funkce najdete v tématu [bodu 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37.  
  
-   **OMP_DYNAMIC** proměnné, naleznete v prostředí [části 4.3](../../parallel/openmp/4-3-omp-dynamic.md) na stránce 49.  
  
-   **omp_in_parallel –** funkce najdete v tématu [části 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) na stránce 38.