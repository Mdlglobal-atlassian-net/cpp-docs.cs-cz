---
title: 4.3 OMP_DYNAMIC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 103067b28990854fb6522c19f4349a9607d65bab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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