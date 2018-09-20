---
title: Direktivy jazyka OpenMP | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0562c263-344c-466d-843e-de830d918940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 983a71920e9e7ce390ab8c64e81886db0d459450
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389444"
---
# <a name="openmp-directives"></a>Direktivy jazyka OpenMP

Obsahuje odkazy na direktivy použité v rozhraní API OpenMP.

Jazyk Visual C++ podporuje následující direktivy OpenMP:

|– Direktiva|Popis|
|---------------|-----------------|
|[atomic](../../../parallel/openmp/reference/atomic.md)|Určuje, že umístění v paměti, která bude aktualizována atomicky.|
|[barrier](../../../parallel/openmp/reference/barrier.md)|Synchronizuje všechna vlákna v týmu; všechna vlákna pozastaví při bariéry, dokud všechna vlákna provést odbourejte překážky bránící.|
|[critical](../../../parallel/openmp/reference/critical.md)|Určuje, že kód je pouze spustit v jednom vlákně najednou.|
|[Vyprázdnění](../../../parallel/openmp/reference/flush-openmp.md)|Určuje, že všechna vlákna stejným zobrazení paměti pro všechny sdílené objekty.|
|[for](../../../parallel/openmp/reference/for-openmp.md)|Způsobí, že během smyčky for uvnitř paralelní oblasti rozdělit mezi vlákny.|
|[master](../../../parallel/openmp/reference/master.md)|Určuje, že pouze hlavní threadshould spustit část programu.|
|[Řazení](../../../parallel/openmp/reference/ordered-openmp-directives.md)|Určuje, že kód v rámci paralelizovaná smyčka by měl být spuštěn jako sekvenční smyčka.|
|[parallel](../../../parallel/openmp/reference/parallel.md)|Definuje paralelní oblasti, což je kód, který spustí paralelně několik vláken.|
|[Oddíly](../../../parallel/openmp/reference/sections-openmp.md)|Identifikuje části kódu k rozdělení mezi všemi vlákny.|
|[single](../../../parallel/openmp/reference/single.md)|Umožňuje určit, že část kódu by měl být provedeny v jednom vlákně, ne tedy nutně hlavní vlákno.|
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|Určuje, že proměnná je privátní pro vlákno.|

## <a name="see-also"></a>Viz také

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)