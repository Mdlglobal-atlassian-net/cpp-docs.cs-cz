---
title: Direktivy jazyka OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0562c263-344c-466d-843e-de830d918940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7421f397b39c6d26c2e60042b25f37277afa5fd
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="openmp-directives"></a>Direktivy jazyka OpenMP
Obsahuje odkazy na direktivy použité v rozhraní API OpenMP.  
  
 Visual C++ podporuje následující direktivy OpenMP:  
  
|– Direktiva|Popis|  
|---------------|-----------------|  
|[atomic](../../../parallel/openmp/reference/atomic.md)|Určuje, že umístění paměti, který bude aktualizován atomicky.|  
|[barrier](../../../parallel/openmp/reference/barrier.md)|Synchronizuje všechna vlákna v týmu; všechna vlákna pozastaví při bariéry, dokud všechna vlákna provést bariéry.|  
|[critical](../../../parallel/openmp/reference/critical.md)|Určuje, zda kód je spustit pouze na jedno vlákno najednou.|  
|[Vyprázdnění](../../../parallel/openmp/reference/flush-openmp.md)|Určuje, že všechna vlákna mají stejné zobrazení paměti pro všechny sdílené objekty.|  
|[for](../../../parallel/openmp/reference/for-openmp.md)|Způsobí, že práci pro smyčky uvnitř paralelní oblast, kterou chcete rozdělit mezi vláken.|  
|[master](../../../parallel/openmp/reference/master.md)|Určuje, spouštění jenom hlavní threadshould oddíl programu.|  
|[řazení](../../../parallel/openmp/reference/ordered-openmp-directives.md)|Určuje tento kód v části parallelized pro smyčky by měl být spuštěn jako sekvenční smyčky.|  
|[parallel](../../../parallel/openmp/reference/parallel.md)|Definuje paralelní oblasti, která je kód, který budou spuštěny několik vláken současně.|  
|[Oddíly](../../../parallel/openmp/reference/sections-openmp.md)|Určuje kód oddíly pro rozdělí mezi všechna vlákna.|  
|[single](../../../parallel/openmp/reference/single.md)|Umožňuje určit, zda se má provést části kódu, na jedno vlákno, nikoli nutně hlavní vlákno.|  
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|Určuje, že je na vlákno soukromé proměnné.|  
  
## <a name="see-also"></a>Viz také  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)