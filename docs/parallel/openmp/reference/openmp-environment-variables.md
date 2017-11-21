---
title: "OpenMP – proměnné prostředí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 18e608862d59357ae26ff918b6b6a1c8b903b270
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="openmp-environment-variables"></a>OpenMP – proměnné prostředí
Obsahuje odkazy na proměnné prostředí použít v rozhraní API OpenMP.  
  
 Visual C++ implementace standardní OpenMP zahrnuje následující proměnné prostředí. Při spuštění programu se čtou těchto proměnných prostředí a úpravy, aby se jejich hodnoty jsou ignorovány za běhu (například pomocí [_putenv –, _wputenv –](../../../c-runtime-library/reference/putenv-wputenv.md)).  
  
|Proměnné prostředí|Popis|  
|--------------------------|-----------------|  
|[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|Určuje, zda OpenMP běh můžete upravit počet vláken v paralelní oblasti.|  
|[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)|Určuje, zda je vnořené paralelismus povoleno, není-li povoleno nebo zakázáno s vnořené paralelismus `omp_set_nested`.|  
|[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|Nastaví maximální počet vláken v oblasti paralelní, není-li přepsat [omp_set_num_threads –](../../../parallel/openmp/reference/omp-set-num-threads.md) nebo [num_threads](../../../parallel/openmp/reference/num-threads.md).|  
|[OMP_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|Mění chování [plán](../../../parallel/openmp/reference/schedule.md) klauzule při `schedule(runtime)` je uveden v `for` nebo `parallel for` – direktiva.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihoven](../../../parallel/openmp/reference/openmp-library-reference.md)