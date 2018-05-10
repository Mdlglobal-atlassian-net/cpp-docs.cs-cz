---
title: Funkce jazyka OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a39fe44ff053a2e49a1067d0af071353e0a50ece
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="openmp-functions"></a>Funkce jazyka OpenMP
Obsahuje odkazy na funkce jazyka OpenMP rozhraní API.  
  
 Visual C++ implementace standardní OpenMP zahrnuje následující funkce.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|Uninitializes zámek.|  
|[omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|Uninitializes nestable zámku.|  
|[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|Vrátí hodnotu, která určuje, pokud počet vláken, která je k dispozici v dalších paralelní oblasti lze upravit podle času spuštění.|  
|[omp_get_max_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|Vrátí celé číslo, které je rovna nebo větší než počet vláken, které by byly k dispozici, pokud paralelní oblast bez [num_threads](../../../parallel/openmp/reference/num-threads.md) nebyly definované v tomto bodě v kódu.|  
|[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)|Vrátí hodnotu, která určuje, zda je povoleno vnořené stupně paralelního zpracování.|  
|[omp_get_num_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|Vrátí počet procesorů, které jsou k dispozici, když je tato funkce volána.|  
|[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|Vrátí počet vláken v paralelní oblasti.|  
|[omp_get_thread_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|Vrátí počet vláken provádění vlákna v rámci jeho team přístup z více vláken.|  
|[omp_get_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|Vrátí počet sekund mezi počtu taktů procesoru.|  
|[omp_get_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|Vrátí že hodnotu v sekundách čas uplynul z některé bodu.|  
|[omp_in_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|Vrátí nenulové hodnoty, pokud je volána v rámci paralelní oblast.|  
|[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)|Inicializuje jednoduché zámku.|  
|[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|Inicializuje zámek.|  
|[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|Označuje, že počet vláken, která je k dispozici v dalších paralelní oblasti lze upravit podle času spuštění.|  
|[omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)|Bloky vláken provádění, dokud nebude k dispozici zámek.|  
|[omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|Bloky vláken provádění, dokud nebude k dispozici zámek.|  
|[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)|Vnořené paralelismus umožňuje.|  
|[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|Nastaví počet vláken v následujících oblastech paralelní, není-li přepsat [num_threads](../../../parallel/openmp/reference/num-threads.md) klauzule.|  
|[omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)|Pokusí se nastavit zámek ale neblokuje provádění vlákna.|  
|[omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|Pokusí se nastavit zámek nestable ale neblokuje provádění vlákna.|  
|[omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|Uvolní zámek.|  
|[omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|Uvolní nestable zámek.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihoven](../../../parallel/openmp/reference/openmp-library-reference.md)