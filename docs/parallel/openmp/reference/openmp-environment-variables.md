---
title: OpenMP – proměnné prostředí | Dokumentace Microsoftu
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
ms.openlocfilehash: 98b61535fd07066c4a1ee24658fdfe81047efc90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446566"
---
# <a name="openmp-environment-variables"></a>OpenMP – proměnné prostředí

Obsahuje odkazy na proměnné prostředí použít v rozhraní API OpenMP.

Implementace jazyka Visual C++, OpenMP standard zahrnuje následující proměnné prostředí. Tyto proměnné prostředí jsou načteny při spuštění programu a změny jejich hodnoty jsou ignorovány za běhu (například pomocí [_putenv _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Proměnná prostředí|Popis|
|--------------------------|-----------------|
|[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|Určuje, zda OpenMP běhu můžete upravit počet vláken v paralelní oblasti.|
|[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)|Určuje, zda je vnořené paralelismu povoleno, není-li povolit nebo zakázat pomocí vnořených paralelismu `omp_set_nested`.|
|[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|Nastaví maximální počet vláken v paralelní oblasti, pokud není přepsán [omp_set_num_threads –](../../../parallel/openmp/reference/omp-set-num-threads.md) nebo [num_threads](../../../parallel/openmp/reference/num-threads.md).|
|[OMP_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|Upravuje chování [plán](../../../parallel/openmp/reference/schedule.md) klauzule při `schedule(runtime)` je zadán v `for` nebo `parallel for` – direktiva.|

## <a name="see-also"></a>Viz také

[Referenční dokumentace knihoven](../../../parallel/openmp/reference/openmp-library-reference.md)