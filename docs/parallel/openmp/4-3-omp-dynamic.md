---
title: 4.3 OMP_DYNAMIC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f376fe639d9bca58b6e2bd55fd081b88921a7342
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686669"
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC
**OMP_DYNAMIC** proměnnou prostředí povolí nebo zakáže dynamické přizpůsobení počet vláken, které jsou k dispozici pro spouštění paralelní oblastí, pokud není explicitně povolená nebo zakázaná voláním Dynamicképřizpůsobení**omp_set_dynamic –** rutiny knihovny. Její hodnota musí být **TRUE** nebo **FALSE**.  
  
 Pokud nastavena na **TRUE**, může upravit počet vláken, které se používají pro provádění paralelního oblasti běhové prostředí nejlépe využívat systémové prostředky.  Pokud nastavena na **FALSE**, dynamické přizpůsobení je zakázána. Výchozí podmínku je definované implementací.  
  
 Příklad:  
  
```  
setenv OMP_DYNAMIC TRUE  
```  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   Další informace o paralelní oblasti, najdete v části [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.  
  
-   **omp_set_dynamic –** funkce najdete v tématu [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.