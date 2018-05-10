---
title: 4.1 OMP_SCHEDULE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e13332077a40e741f56b5602ac5197bbdfef071
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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