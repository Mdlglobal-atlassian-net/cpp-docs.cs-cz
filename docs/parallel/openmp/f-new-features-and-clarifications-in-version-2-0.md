---
title: F. Nové funkce a vyjasnění ve verzi 2.0
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 8cd82000992ab957bf2c41f11deccd65e2e6ea8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215030"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nové funkce a vyjasnění ve verzi 2.0

V tomto dodatku jsou shrnuty klíčové změny, které byly provedeny vC++ rámci specifikace OpenMP C/při přesunu z verze 1,0 na verzi 2,0. Následující položky jsou nové funkce přidané do specifikace:

- V [direktivách](2-directives.md#21-directive-format)OpenMP jsou povoleny čárky.

- Přidání klauzule `num_threads`. Tato klauzule umožňuje uživateli požádat o konkrétní počet vláken pro [paralelní konstrukci](2-directives.md#23-parallel-construct).

- Direktiva [threadprivate](2-directives.md#271-threadprivate-directive) se rozšířila tak, aby přijímala statické proměnné rozsahu bloku.

- Pole s proměnnou délkou C99 jsou kompletní typy a dají se zadat všude, kde jsou povolené typy, například v seznamech `private`, `firstprivate`a `lastprivate` (viz [oddíl 2.7.2](2-directives.md#272-data-sharing-attribute-clauses)).

- Soukromá proměnná v paralelní oblasti může být ve vnořené direktivě označena jako [soukromá](2-directives.md#2721-private) .

- Byla přidána klauzule `copyprivate`. Poskytuje mechanismus pro použití soukromé proměnné pro vysílání hodnoty od jednoho člena týmu do ostatních členů. Je alternativou k použití sdílené proměnné pro hodnotu, pokud by byla taková sdílená proměnná obtížné (například v rekurzi vyžadující jinou proměnnou na každé úrovni). Klauzule [copyprivate](2-directives.md#2728-copyprivate) se může vyskytovat pouze v direktivě `single`.

- Přidání rutin časování [omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function) a [omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) podobně jako rutiny MPI. Tyto funkce jsou nezbytné k časování hodin na zdi.

- Byl přidán dodatek se seznamem [chování definovaného implementací](e-implementation-defined-behaviors-in-openmp-c-cpp.md) v OpenMP C/C++ . Implementace je nutná k definování a dokumentaci jeho chování v těchto případech.

- Následující změny slouží k objasnění nebo opravě funkcí v předchozí specifikaci rozhraní OpenMP API pro CC++/:

  - Vyjasněno, že chování [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) a [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) , pokud `omp_in_parallel` vrátí nenulovou hodnotu, není definováno.

  - Vyjasněná [vnořená direktiva](2-directives.md#29-directive-nesting) při použití vnořené paralelní funkce.

  - Funkce [inicializace zámku](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) a [zničení zámku](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) lze volat v paralelní oblasti.

  - Do [přílohy A](a-examples.md)byly přidány nové příklady.
