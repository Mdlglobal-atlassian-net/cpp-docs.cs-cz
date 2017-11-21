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
ms.openlocfilehash: 2b23719d1559a00b807f724a3e31eb7b673a5a17
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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