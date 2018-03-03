---
title: 4.1 OMP_SCHEDULE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 330e5ea576e3cd779a7c17c21d00b6459f5e7043
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE
**OMP_SCHEDULE** se vztahují pouze na **pro** a **paralelní pro** direktivy, které mají typ plánu **runtime**. Plán typu a bloku velikost pro všechny tyto smyčky můžete nastavit v době běhu nastavením této proměnné prostředí pro jakýkoli z typů rozpoznaný plán a volitelné *chunk_size*.  
  
 Pro **pro** a **paralelní pro** direktivy, které mají typ plánu jiné než **runtime**, **OMP_SCHEDULE** je ignorována. Výchozí hodnota pro tuto proměnnou prostředí je definované implementací. Pokud volitelné *chunk_size* nastaven, hodnota musí být kladná. Pokud *chunk_size* není nastaven, je použita hodnota 1, s výjimkou u **statické** plán. Pro **statické** , výchozí velikost bloku je nastavit plán do prostoru iteraci smyčky dělený počet vláken u smyčky.  
  
 Příklad:  
  
```  
setenv OMP_SCHEDULE "guided,4"  
setenv OMP_SCHEDULE "dynamic"  
```  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **pro** direktivy, viz [části 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stránce 11.  
  
-   **paralelní pro** direktivy, viz [části 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) na stránce 16.