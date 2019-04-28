---
title: F. Nové funkce a vyjasnění ve verzi 2.0
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 2e186bbc82f4f43e831dd05cdded2a9e946d1dd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362709"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nové funkce a vyjasnění ve verzi 2.0

Tento dodatek obsahuje souhrn klíčových změny specifikace OpenMP – C/C++ při přesunu z verze 1.0 na verzi 2.0. Následující položky jsou nové funkce přidané ve specifikaci:

- Čárky jsou povoleny v OpenMP [direktivy](2-directives.md#21-directive-format).

- Přidání `num_threads` klauzuli. Umožňuje uživatelům požádat o určitý počet vláken pro tuto klauzuli [paralelní konstrukce](2-directives.md#23-parallel-construct).

- [Threadprivate](2-directives.md#271-threadprivate-directive) směrnice bylo rozšířeno tak, aby přijímal rozsahu bloku statické proměnné.

- Pole proměnné délky C99 jsou kompletními typy a je možné zadat kdekoli kompletními typy jsou povolené, například seznamy `private`, `firstprivate`, a `lastprivate` klauzule (naleznete v tématu [části 2.7.2](2-directives.md#272-data-sharing-attribute-clauses)).

- Soukromé proměnné v paralelní oblasti může být označený [privátní](2-directives.md#2721-private) znovu za vnořená direktiva.

- `copyprivate` Klauzule se přidala. Poskytuje mechanismus pro používat soukromé proměnné k ostatním členům vysílání hodnotu z jednoho člena týmu. Jde o alternativu k použití sdílené proměnné pro hodnotu při poskytování sdílené proměnné by bylo obtížné (například v rekurze vyžadující jinou proměnnou na každé úrovni). [Copyprivate](2-directives.md#2728-copyprivate) klauzule může vyskytovat jenom u `single` směrnice.

- Přidání rutiny časování [omp_get_wtick –](3-run-time-library-functions.md#332-omp_get_wtick-function) a [omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) podobně jako rutiny MPI. Tyto funkce jsou nezbytné pro stěn taktování.

- Dodatek seznam [chování definované implementací](e-implementation-defined-behaviors-in-openmp-c-cpp.md) byly přidány OpenMP – C/C++. Implementace je potřeba definovat a dokumentovat jeho chování v těchto případech.

- Následující změny slouží k vysvětlení nebo opravte funkce v předchozí specifikace OpenMP – rozhraní API pro C/C++:

  - Vyjasněno, že chování [omp_set_nested –](3-run-time-library-functions.md#319-omp_set_nested-function) a [omp_set_dynamic –](3-run-time-library-functions.md#317-omp_set_dynamic-function) při `omp_in_parallel` vrátí nenulovou hodnotu není definován.

  - Obsahuje upřesnění [vnořování direktiv](2-directives.md#29-directive-nesting) při použití vnořených současně.

  - [Zamknout inicializace](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) a [zamknout zničení](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) funkce mohou být volány v paralelní oblasti.

  - Přibyla nová příklady [příloha A](a-examples.md).