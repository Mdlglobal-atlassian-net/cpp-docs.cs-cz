---
title: Direktivy jazyka OpenMP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0562c263-344c-466d-843e-de830d918940
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 21cb751c4ee4c261db1d6a4d5efda49a1445ade7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="openmp-directives"></a>Direktivy jazyka OpenMP
Obsahuje odkazy na direktivy použité v rozhraní API OpenMP.  
  
 Visual C++ podporuje následující direktivy OpenMP:  
  
|– Direktiva|Popis|  
|---------------|-----------------|  
|[Atomic](../../../parallel/openmp/reference/atomic.md)|Určuje, že umístění paměti, který bude aktualizován atomicky.|  
|[Barrier](../../../parallel/openmp/reference/barrier.md)|Synchronizuje všechna vlákna v týmu; všechna vlákna pozastaví při bariéry, dokud všechna vlákna provést bariéry.|  
|[kritické](../../../parallel/openmp/reference/critical.md)|Určuje, zda kód je spustit pouze na jedno vlákno najednou.|  
|[vyprázdnění](../../../parallel/openmp/reference/flush-openmp.md)|Určuje, že všechna vlákna mají stejné zobrazení paměti pro všechny sdílené objekty.|  
|[pro](../../../parallel/openmp/reference/for-openmp.md)|Způsobí, že práci pro smyčky uvnitř paralelní oblast, kterou chcete rozdělit mezi vláken.|  
|[hlavní server](../../../parallel/openmp/reference/master.md)|Určuje, spouštění jenom hlavní threadshould oddíl programu.|  
|[řazení](../../../parallel/openmp/reference/ordered-openmp-directives.md)|Určuje tento kód v části parallelized pro smyčky by měl být spuštěn jako sekvenční smyčky.|  
|[paralelní](../../../parallel/openmp/reference/parallel.md)|Definuje paralelní oblasti, která je kód, který budou spuštěny několik vláken současně.|  
|[oddíly](../../../parallel/openmp/reference/sections-openmp.md)|Určuje kód oddíly pro rozdělí mezi všechna vlákna.|  
|[jeden](../../../parallel/openmp/reference/single.md)|Umožňuje určit, zda se má provést části kódu, na jedno vlákno, nikoli nutně hlavní vlákno.|  
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|Určuje, že je na vlákno soukromé proměnné.|  
  
## <a name="see-also"></a>Viz také  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)