---
title: E. Chování definované implementací v jazyce C/C++ v prostředí OpenMP
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: e866eee9c6d85e93388f9f1d086badf948e2600e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215043"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Chování definované implementací v jazyce C/C++ v prostředí OpenMP

V tomto dodatku jsou shrnuta chování, která jsou v tomto rozhraní API popsána jako "definovaná implementací".  Každé chování se křížově odkazuje zpátky na jeho popis v hlavní specifikaci.

## <a name="remarks"></a>Poznámky

Implementace je nutná k definování a dokumentaci jeho chování v těchto případech, ale tento seznam může být neúplný.

- **Počet vláken:** Pokud je k dispozici paralelní oblast v době, kdy je zakázána dynamická úprava počtu vláken, a počet vláken, která jsou požadována pro paralelní oblast, je větší než počet, který může systém run-time dodat, chování programu je definováno (viz stránka 9).

   V vizuálu C++se pro nevnořenou paralelní oblast zobrazí 64 vláken (maximum).

- **Počet procesorů:** Počet fyzických procesorů, které jsou aktuálně hostiteli vláken v daném čase, je definován implementací (viz stránka 10).

   V jazyce C++Visual není toto číslo konstantní a řídí se operačním systémem.

- **Vytváření týmů vláken:** Počet vláken v týmu, který spouští vnořenou paralelní oblast, je definován implementací (viz stránka 10).

   V jazyce C++Visual je toto číslo určeno operačním systémem.

- **plán (Runtime):** Rozhodnutí o plánování je odloženo až do doby běhu. Typ plánu a velikost bloku lze vybrat za běhu nastavením proměnné prostředí `OMP_SCHEDULE`. Pokud tato proměnná prostředí není nastavena, je výsledný plán definován implementací (viz stránka 13).

   V jazyce C++Visual je typ plánu `static` bez velikosti bloku.

- **Výchozí plánování:** V případě absence klauzule Schedule je výchozí plán definován implementací (viz strana 13).

   Ve vizuálu C++je výchozí typ plánu `static` bez velikosti bloku.

- **Atomická:** Implementace je definovaná bez ohledu na to, jestli implementace nahrazuje všechny direktivy `atomic` `critical` direktivami, které mají stejný jedinečný název (viz stránka 20).

   Pokud se C++v vizuálu data upravená [atomicky](reference/openmp-directives.md#atomic) netýkají přirozeného zarovnání, nebo pokud je jeden nebo dva bajty dlouhé, všechny atomické operace, které tuto vlastnost vyhoví, budou používat jednu kritickou část. V opačném případě se nepoužijí kritické oddíly.

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** Pokud byl počet vláken explicitně nastaven uživatelem, je výchozí hodnota definovaná implementací (viz stránka 9).

   Ve vizuálu C++je výchozí počet vláken roven počtu procesorů.

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** Výchozí hodnota pro úpravu dynamického vlákna je definovaná implementací.

   Ve vizuálu C++je výchozí hodnota `FALSE`.

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** Je-li povolen vnořený paralelismus, je počet vláken použitých k provedení vnořených paralelních oblastí definován implementací.

   V jazyce C++Visual je počet vláken určený operačním systémem.

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) proměnná prostředí: výchozí hodnota pro tuto proměnnou prostředí je definovaná implementací.

   V jazyce C++Visual je typ plánu `static` bez velikosti bloku.

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) proměnná prostředí: Pokud není zadána žádná hodnota pro proměnnou prostředí `OMP_NUM_THREADS`, nebo pokud zadaná hodnota není kladné celé číslo, nebo pokud je hodnota větší než maximální počet vláken, která může systém podporovat, je počet vláken, která se mají použít, definovaná implementací.

   Pokud je C++hodnota zadaná v vizuálu nula nebo menší, počet vláken se rovná počtu procesorů.  Pokud je hodnota větší než 64, počet vláken je 64.

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) proměnná prostředí: výchozí hodnota je definovaná implementací.

   Ve vizuálu C++je výchozí hodnota `FALSE`.
