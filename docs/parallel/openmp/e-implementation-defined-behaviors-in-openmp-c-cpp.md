---
title: E. Chování definované implementací v OpenMP – C/C++
ms.date: 11/04/2016
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: 704062f36102a06e6e7b8cf015f6330f925a6bba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619346"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Chování definované implementací v OpenMP – C/C++

Tento dodatek shrnuje chování, které jsou popsány jako "definované implementací" v tomto rozhraní API.  Každý chování je zpět do její popis ve specifikaci hlavní křížovými odkazy.

## <a name="remarks"></a>Poznámky

Implementace je potřeba definovat a jeho chování v těchto případech dokumentu, ale tento seznam nemusí být úplný.

- **Počet vláken:** Pokud paralelní oblasti je při došlo k chybě dynamické úpravy počtu vláken je zakázané, a počet vláken pro paralelní oblasti požaduje překračuje počet, který můžete zadat systému za běhu, chování program je definované implementací (viz stránka 9).

   V jazyce Visual C++ pro nevnořený paralelní oblasti, 64 vlákna (maximum), poskytneme vám.

- **Počet procesorů:** počet fyzických procesorů ve skutečnosti hostování vlákna v daném okamžiku je definované implementací (viz stránka 10).

   V jazyce Visual C++ toto číslo není konstantní a řídí operační systém.

- **Vytváření týmů vláken:** je počet vláken v týmu, které jsou spuštěny paralelní vnořené oblasti definované implementací. () Viz stránka 10).

   V jazyce Visual C++ se určuje podle operačního systému.

- **Schedule(runtime):** rozhodnutí týkající se plánování je odložena až do doby běhu. Typ a bloků velikosti plán lze vybrat v době běhu tak, že nastavíte `OMP_SCHEDULE` proměnné prostředí. Pokud tato proměnná prostředí není nastavená, výsledný plán je definované implementací (viz stránka 13).

   V jazyce Visual C++ je typ plánu `static` s žádná velikost bloku.

- **Plánování výchozí:** chybí klauzule schedule, výchozí plán je definované implementací (viz stránka 13).

   V jazyce Visual C++, je výchozí typ plánu `static` s žádná velikost bloku.

- **Ten:** je definováno implementací Určuje, zda implementace nahradí všechny `atomic` direktivy s **kritické** direktivy, které mají stejný jedinečný název (viz stránka 20).

   V jazyce Visual C++, pokud data změnil [atomické](../../parallel/openmp/reference/atomic.md) není na přirozeného zarovnání. nebo pokud je 1 nebo 2 bajty dlouhý všechny atomických operací, které splňují tuto vlastnost použije jeden kritický oddíl. Kritické oddíly, jinak nebudou použity.

- **omp_get_num_threads:** Pokud počet vláken není nastavený explicitně uživatelem, výchozí hodnota je definováno implementací (viz stránka 9, a [části 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37).

   V jazyce Visual C++ se rovná počtu procesorů výchozí počet vláken.

- **omp_set_dynamic –:** výchozí nastavení pro úpravu dynamické vlákno je definováno implementací (viz [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39).

   V jazyce Visual C++, výchozí hodnota je `FALSE`.

- **omp_set_nested –:** obrysů vnořené paralelismu, počet podprocesů používaný k provedení vnořených paralelních oblastí je definováno implementací (viz [části 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stránce 40).

   V jazyce Visual C++ je určen počet vláken v operačním systému.

- `OMP_SCHEDULE` proměnné prostředí: výchozí hodnota této proměnné prostředí, je definováno implementací (viz [části 4.1](../../parallel/openmp/4-1-omp-schedule.md) na stránce 48).

   V jazyce Visual C++ je typ plánu `static` s žádná velikost bloku.

- `OMP_NUM_THREADS` proměnné prostředí: Pokud není zadána žádná hodnota pro `OMP_NUM_THREADS` proměnné prostředí, nebo pokud zadaná hodnota není kladné celé číslo, nebo pokud je hodnota větší než maximální počet vláken, může systém podporovat, je počet vláken definované implementací (viz [části 4.2](../../parallel/openmp/4-2-omp-num-threads.md) na stránce 48).

   V jazyce Visual C++ Pokud zadaná hodnota je nula nebo méně, je počet vláken rovná počtu procesorů.  Pokud je hodnota větší než 64, počet vláken je 64.

- `OMP_DYNAMIC` proměnné prostředí: výchozí hodnota je definováno implementací (viz [části 4.3](../../parallel/openmp/4-3-omp-dynamic.md) na stránce 49).

   V jazyce Visual C++, výchozí hodnota je `FALSE`.