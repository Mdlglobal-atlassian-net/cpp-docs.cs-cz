---
title: OpenMP – proměnné prostředí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02248b7725f2a4312f26984c798e7248463d2615
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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