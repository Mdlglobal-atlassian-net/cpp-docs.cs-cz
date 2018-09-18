---
title: OMP_NUM_THREADS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NUM_THREADS
dev_langs:
- C++
helpviewer_keywords:
- OMP_NUM_THREADS OpenMP environment variable
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39f45b9c81d5339b2b6afe4c77fdc9bac6b5d731
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091163"
---
# <a name="ompnumthreads"></a>OMP_NUM_THREADS
Nastaví maximální počet vláken v paralelní oblasti, pokud není přepsán [omp_set_num_threads –](../../../parallel/openmp/reference/omp-set-num-threads.md) nebo [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
### <a name="parameters"></a>Parametry
  
*počet*<br/>
Maximální počet vláken, které chcete v paralelní oblasti až 64 v implementaci Visual C++.  
  
## <a name="remarks"></a>Poznámky  
 **OMP_NUM_THREADS** proměnné prostředí můžete přepsat [omp_set_num_threads –](../../../parallel/openmp/reference/omp-set-num-threads.md) funkce nebo [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
 Výchozí hodnota `num` v jazyce Visual C++ implementace standardu OpenMP je počet virtuálních procesorů, včetně hyperthreadingem procesory.  
  
 Další informace najdete v tématu [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).  
  
## <a name="example"></a>Příklad  
 Nastaví zadáním následujícího příkazu **OMP_NUM_THREADS** proměnné prostředí na 16:  
  
```  
set OMP_NUM_THREADS=16  
```  
  
 Následující příkaz zobrazí aktuální nastavení **OMP_NUM_THREADS** proměnné prostředí:  
  
```  
set OMP_NUM_THREADS  
```  
  
## <a name="see-also"></a>Viz také  
 [Proměnné prostředí](../../../parallel/openmp/reference/openmp-environment-variables.md)