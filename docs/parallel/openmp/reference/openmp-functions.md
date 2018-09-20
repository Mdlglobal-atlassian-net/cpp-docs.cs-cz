---
title: Funkce jazyka OpenMP | Dokumentace Microsoftu
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
ms.openlocfilehash: a5daa7737f63df437f31f349a85811befe0c8f5b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425597"
---
# <a name="openmp-functions"></a>Funkce jazyka OpenMP

Obsahuje odkazy na funkcí používaných v rozhraní API OpenMP.

Implementace jazyka Visual C++, OpenMP standard zahrnuje následující funkce.

|Funkce|Popis|
|--------------|-----------------|
|[omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|Zruší inicializaci zámek.|
|[omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|Zruší inicializaci, vnořitelných zámek.|
|[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|Vrátí hodnotu určující, pokud je možné upravit počet vláken v následných paralelní oblasti podle času spuštění.|
|[omp_get_max_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|Vrátí celé číslo, které je roven nebo větší než počet vláken, která bude k dispozici, pokud paralelní oblasti bez [num_threads](../../../parallel/openmp/reference/num-threads.md) nebyly definované v tomto bodě v kódu.|
|[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)|Vrátí hodnotu, která označuje, zda je povoleno vnořené paralelismu.|
|[omp_get_num_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|Vrátí počet procesorů, které jsou k dispozici, když je tato funkce volána.|
|[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|Vrátí počet vláken v paralelní oblasti.|
|[omp_get_thread_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|Vrátí počet vláken vlákno provádění v rámci týmu jeho vlákna.|
|[omp_get_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|Vrátí počet sekund mezi cykly hodin procesoru.|
|[omp_get_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|Vrátí že hodnotu v sekundách času uplynulo v určitém okamžiku.|
|[omp_in_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|Vrátí nenulovou hodnotu, je-li volat v rámci paralelní oblasti.|
|[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)|Inicializuje jednoduchým zámkem.|
|[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|Inicializuje zámek.|
|[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|Označuje, že je možné upravit počet vláken v následných paralelní oblasti podle času spuštění.|
|[omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)|Bloky spouštění vlákna, dokud se zámek je k dispozici.|
|[omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|Bloky spouštění vlákna, dokud se zámek je k dispozici.|
|[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)|Povolí vnořená paralelismu.|
|[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|Nastaví počet vláken v následných paralelních oblastí, pokud nejsou přepsány [num_threads](../../../parallel/openmp/reference/num-threads.md) klauzuli.|
|[omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)|Pokusí se nastavit zámek, ale neblokuje spouštění vláken.|
|[omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|Pokusí se nastavit, vnořitelných zámek, ale neblokuje vlákno provádění.|
|[omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|Uvolní zámek.|
|[omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|Uvolní, vnořitelných zámek.|

## <a name="see-also"></a>Viz také

[Referenční dokumentace knihoven](../../../parallel/openmp/reference/openmp-library-reference.md)