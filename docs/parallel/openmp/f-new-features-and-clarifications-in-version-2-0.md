---
title: "F. Nové funkce a objasnění, která ve verzi 2.0 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b9a661f183816fec0f7a71c990f1508338100f4d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nové funkce a objasnění, která ve verzi 2.0
Tento dodatek shrnuje klíče změny provedené v specifikace OpenMP C/C++ při přesouvání z verze 1.0 na verzi 2.0. Následující položky jsou nové funkce přidané do specifikace:  
  
-   Čárky jsou povolena ve direktivy OpenMP ([části 2.1](../../parallel/openmp/2-1-directive-format.md) na stránce 7).  
  
-   Přidání `num_threads` klauzule. Tuto klauzuli umožňuje uživatelům požádat o určitý počet vláken pro paralelní konstrukce ([části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8).  
  
-   `threadprivate` – Direktiva rozšířilo tak, aby přijímal statický rozsah bloku proměnné ([části 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) na stránce 23).  
  
-   Délka pole proměnných C99 jsou dokončení typy a proto mohou být zadány kdekoli dokončení typy jsou povoleny, například v seznamy `private`, `firstprivate`, a `lastprivate` – klauzule ([části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25).  
  
-   Soukromé proměnné v paralelní oblasti může být označen privátní znovu za vnořené – direktiva ([části 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stránce 25).  
  
-   `copyprivate` Klauzule byla přidána. Poskytuje mechanismus pro použití soukromé proměnné k vysílání hodnotu z jednoho člena týmu ostatním členům. Jde o alternativu k použití sdílené proměnné pro hodnotu, při poskytování sdílené proměnné může být obtížné (například v rekurze, vyžadování jiné proměnné na každé úrovni). `copyprivate` Klauzule se může vyskytovat pouze na **jeden** – direktiva ([části 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stránce 32).  
  
-   Přidání rutiny časování `omp_get_wtick` a `omp_get_wtime` podobná MPI rutiny. Tyto funkce jsou nezbytné pro provádění wall taktování ([části 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md) na stránce 44 a [části 3.3.2](../../parallel/openmp/3-3-2-omp-get-wtick-function.md) na stránce 45).  
  
-   Dodatek seznam chování definované implementací v OpenMP C/C++ byla přidána. Implementace je potřeba definovat a zdokumentovat své chování v těchto případech ([příloha E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md) na stránce 97).  
  
-   Vysvětlení nebo opravte funkce ve specifikaci předchozí OpenMP rozhraní API pro C/C++ mají následující změny:  
  
    -   Vyjasněno, že chování `omp_set_nested` a `omp_set_dynamic` při `omp_in_parallel` vrátí nenulovou není definován ([části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39, a [části 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stránce 40).  
  
    -   Pokud se používá paralelní vnořené vyjasněno vnořování direktiv ([části 2.9](../../parallel/openmp/2-9-directive-nesting.md) na stránce 33).  
  
    -   Funkce Zámek inicializace a zámek odstraňování lze volat v paralelní oblasti ([části 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) na stránce 42 a [části 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) na stránce 42).  
  
    -   Byly přidány nové příklady ([příloha A](../../parallel/openmp/a-examples.md) na stránce 51).