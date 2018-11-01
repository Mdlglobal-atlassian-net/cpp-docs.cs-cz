---
title: F. Nové funkce a vyjasnění ve verzi 2.0
ms.date: 11/04/2016
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: c8a597c6af397bd162d92a945d96409b1839e2a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657145"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nové funkce a vyjasnění ve verzi 2.0

Tento dodatek obsahuje souhrn klíčových změny specifikace OpenMP – C/C++ při přesunu z verze 1.0 na verzi 2.0. Následující položky jsou nové funkce přidané ve specifikaci:

- Čárky jsou povolené v direktivy OpenMP ([části 2.1](../../parallel/openmp/2-1-directive-format.md) na stránce 7).

- Přidání `num_threads` klauzuli. Tato klauzule umožňuje uživatelům požádat o určitý počet vláken pro paralelní konstrukce ([části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8).

- `threadprivate` Směrnice bylo rozšířeno tak, aby přijímal rozsahu bloku statické proměnné ([části 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) na stránce 23).

- Pole proměnné délky C99 jsou kompletními typy a proto je možné zadat kdekoli kompletní povolené jsou typy, například v seznamech `private`, `firstprivate`, a `lastprivate` klauzule ([části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25).

- Soukromé proměnné v paralelní oblasti je možné označit privátní znovu ve vnořených – direktiva ([části 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stránce 25).

- `copyprivate` Klauzule se přidala. Poskytuje mechanismus pro používat soukromé proměnné k ostatním členům vysílání hodnotu z jednoho člena týmu. Jde o alternativu k použití sdílené proměnné pro hodnotu při poskytování sdílené proměnné by bylo obtížné (například v rekurze vyžadující jinou proměnnou na každé úrovni). `copyprivate` Klauzule může vyskytovat jenom u **jeden** – direktiva ([části 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stránce 32).

- Přidání rutiny časování `omp_get_wtick` a `omp_get_wtime` podobně jako rutiny MPI. Tyto funkce jsou nezbytné pro provádění wall taktování ([sekci 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md) na stránce 44 a [části 3.3.2](../../parallel/openmp/3-3-2-omp-get-wtick-function.md) na stránce 45).

- Dodatek seznam chování definované implementací v OpenMP – C/C++ se přidala. Implementace je potřeba definovat a dokumentovat jeho chování v těchto případech ([příloha E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md) na stránce 97).

- Následující změny slouží k vysvětlení nebo opravte funkce v předchozí specifikace OpenMP – rozhraní API pro C/C++:

   - Vyjasněno, že chování `omp_set_nested` a `omp_set_dynamic` při `omp_in_parallel` vrátí nenulovou hodnotu, není definována ([části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39, a [části 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stránce 40).

   - Při použití vnořených paralelní vyjasněno vnořování direktiv ([části 2.9](../../parallel/openmp/2-9-directive-nesting.md) na stránce 33).

   - Funkce Zámek inicializace a zámek odstranění lze volat v paralelní oblasti ([části 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) na stránce 42 a [části 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) na stránce 42).

   - Byly přidány nové příklady ([příloha A](../../parallel/openmp/a-examples.md) na stránce 51).