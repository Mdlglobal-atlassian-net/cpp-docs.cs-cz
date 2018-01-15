---
title: 4.2 OMP_NUM_THREADS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9c2b766d0e3be9b4f1d272a6e3fa205cfcb87039
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS
**OMP_NUM_THREADS** proměnnou prostředí nastaví výchozí počet vláken používaných při spuštění, pokud toto číslo je explicitně změnit voláním **omp_set_num_threads –** rutiny knihovny nebo podle explicitního **num_threads** klauzule ve **paralelní** – direktiva.  
  
 Hodnota **OMP_NUM_THREADS** proměnnou prostředí musí být kladné celé číslo. Jeho dopad závisí na tom, jestli je dynamické přizpůsobení počet vláken, povolena. Pro komplexní sadu pravidel o interakci mezi **OMP_NUM_THREADS** prostředí proměnné a dynamické úpravy vláken, viz část 2.3 na stránce 8.  
  
 Pokud není zadaná žádná hodnota pro **OMP_NUM_THREADS** proměnné prostředí, nebo pokud zadaná hodnota není celé kladné číslo, nebo pokud je hodnota větší než maximální počet vláken v systému může podporovat, počet vláken používaných je definované implementací.  
  
 Příklad:  
  
```  
setenv OMP_NUM_THREADS 16  
```  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **num_threads** klauzule, najdete v části [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.  
  
-   **omp_set_num_threads –** funkce najdete v tématu [bod 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stránce 36.  
  
-   **omp_set_dynamic –** funkce najdete v tématu [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.