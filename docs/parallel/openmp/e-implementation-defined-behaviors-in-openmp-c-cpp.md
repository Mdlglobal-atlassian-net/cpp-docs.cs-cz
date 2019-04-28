---
title: E. Chování definované implementací v OpenMP – C/C++
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: 3d8e9493cad1fce02e5d482cd5e612afb44bb37b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362751"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Chování definované implementací v OpenMP – C/C++

Tento dodatek shrnuje chování, které jsou popsány jako "definované implementací" v tomto rozhraní API.  Každý chování je zpět do její popis ve specifikaci hlavní křížovými odkazy.

## <a name="remarks"></a>Poznámky

Implementace je potřeba definovat a jeho chování v těchto případech dokumentu, ale tento seznam nemusí být úplný.

- **Počet vláken:** Pokud při dynamické úpravy počtu vláken je zakázaná, a počet vláken, které jsou požadované pro paralelní oblasti je větší než číslo, které můžete zadat systému za běhu je zjištěna paralelní oblasti, je chování programu definované implementací (viz stránka 9).

   V jazyce Visual C++ pro nevnořený paralelní oblasti, 64 vlákna (maximum), poskytneme vám.

- **Počet procesorů:** Počet fyzických procesorů ve skutečnosti hostování vlákna v daném okamžiku je definované implementací (viz stránka 10).

   V jazyce Visual C++ toto číslo není konstantní a řídí operační systém.

- **Vytváření týmů vláken:** Počet vláken v týmu, které jsou spuštěny paralelní vnořené oblasti je definované implementací (viz stránka 10).

   V jazyce Visual C++ toto číslo je určeno v operačním systému.

- **Schedule(runtime):** Rozhodnutí o plánování je odložena až do doby běhu. Typ a bloků velikosti plán lze vybrat v době běhu tak, že nastavíte `OMP_SCHEDULE` proměnné prostředí. Pokud tato proměnná prostředí není nastavená, výsledný plán je definované implementací (viz stránka 13).

   V jazyce Visual C++ je typ plánu `static` s žádná velikost bloku.

- **Výchozí plánování:** Chybí klauzule schedule výchozí plán je definované implementací (viz stránka 13).

   V jazyce Visual C++, je výchozí typ plánu `static` s žádná velikost bloku.

- **ATOMIC:** Je definováno implementací Určuje, zda implementace nahradí všechny `atomic` direktivy s `critical` direktivy, které mají stejný jedinečný název (viz stránka 20).

   V jazyce Visual C++, pokud data změnil [atomické](reference/openmp-directives.md#atomic) není na přirozeného zarovnání. nebo pokud je jeden nebo dva bajty dlouhý, všechny atomických operací, které splňují tuto vlastnost použije jeden kritický oddíl. Kritické oddíly, jinak nebudou použity.

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** Pokud počet vláken není nastavený explicitně uživatelem, výchozí hodnota je definované implementací (viz stránka 9).

   V jazyce Visual C++ se rovná počtu procesorů výchozí počet vláken.

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** Výchozí nastavení pro úpravu dynamické vlákno je definován implementací.

   V jazyce Visual C++, výchozí hodnota je `FALSE`.

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** Pokud je povoleno vnořené paralelismu, počet podprocesů používaný k provedení vnořených paralelních oblastí je definované implementací.

   V jazyce Visual C++ je určen počet vláken v operačním systému.

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) proměnné prostředí: Výchozí hodnota pro tuto proměnnou prostředí je definován implementací.

   V jazyce Visual C++ je typ plánu `static` s žádná velikost bloku.

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) proměnné prostředí: Pokud není zadána žádná hodnota pro `OMP_NUM_THREADS` proměnné prostředí, nebo pokud zadaná hodnota není kladné celé číslo, nebo pokud je hodnota větší než maximální počet vláken, může systém podporovat, počet vláken, je definováno implementací.

   V jazyce Visual C++ Pokud zadaná hodnota je nula nebo méně, je počet vláken rovná počtu procesorů.  Pokud je hodnota větší než 64, počet vláken je 64.

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) proměnné prostředí: Výchozí hodnota je definován implementací.

   V jazyce Visual C++, výchozí hodnota je `FALSE`.