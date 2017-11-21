---
title: "E. Chování v OpenMP C/C++ definované implementací | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d54705947db5125bd9d30adb8a074a6ac354b94a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Chování definované implementací v OpenMP C/C++
Tento dodatek shrnuje chování, které jsou popsány jako "definované implementací" v tomto rozhraní API.  Každý chování je zpět do jeho popis hlavních specifikací křížových odkazů.  
  
## <a name="remarks"></a>Poznámky  
 Implementace je potřeba definovat a její chování v těchto případech dokumentu, ale tento seznam mohou být neúplné.  
  
-   **Počet vláken:** Pokud paralelní oblast je došlo při dynamické přizpůsobení počet vláken je zakázané a počet vláken, které jsou požadované pro paralelní oblast překračuje počet, který běhu systému můžete zadat, chování Tento program je definované implementací (viz stránka 9).  
  
     V jazyce Visual C++ pro-nested paralelní oblast, bude nutné zadat 64 vláken (maximum).  
  
-   **Počet procesorů:** počet fyzických procesorů ve skutečnosti hostování vláken v každém okamžiku je definované implementací (viz stránka 10).  
  
     V jazyce Visual C++ tato hodnota není konstantní a řídí operační systém.  
  
-   **Vytváření týmy vláken:** je počet vláken v týmu, které se spouští paralelní vnořené oblasti definované implementací. () Viz stránka 10).  
  
     V jazyce Visual C++ je určen podle operačního systému.  
  
-   **Schedule(runtime):** rozhodnutí týkající se plánování je odložena až do doby běhu. Velikost plán typu a bloku dat je možné vybrat v době běhu nastavením `OMP_SCHEDULE` proměnné prostředí. Pokud není nastavena tato proměnná prostředí, výsledný plán je definované implementací (viz stránka 13).  
  
     V jazyce Visual C++, typ plánu je `static` s žádné velikost bloku.  
  
-   **Plánování výchozí:** chybí klauzule plán, výchozí plán je definované implementací (viz stránka 13).  
  
     V jazyce Visual C++, je výchozí plán typ `static` s žádné velikost bloku.  
  
-   **Ten:** je definované implementací jestli implementace nahradí všechny `atomic` direktivy s **kritické** direktivy, které mají stejný název jedinečný (viz stránka 20).  
  
     V jazyce Visual C++, pokud data upraveném [atomic](../../parallel/openmp/reference/atomic.md) není na přirozené zarovnání nebo pokud je 1 nebo 2 bajty dlouho všechny atomické operací, které splňují tuto vlastnost použije kritické jeden oddíl. Kritické oddíly, jinak nebudou použity.  
  
-   **omp_get_num_threads –:** Pokud uživatel není explicitně nastavena počet vláken, výchozí hodnota je definované implementací (viz stránka 9, a [bodu 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37).  
  
     V jazyce Visual C++ výchozí počet vláken, se rovná počtu procesorů.  
  
-   **omp_set_dynamic –:** na výchozí hodnoty pro úpravu dynamické vlákno je definované implementací (viz [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39).  
  
     V jazyce Visual C++, výchozí hodnota je `FALSE`.  
  
-   **omp_set_nested –:** Pokud vnořené paralelismus je povoleno, je počet vláken používaných provést paralelní vnořené oblasti definované implementací (viz [části 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stránce 40).  
  
     V jazyce Visual C++ počet vláken, je dáno operačního systému.  
  
-   `OMP_SCHEDULE`proměnné prostředí: výchozí hodnota pro tuto proměnnou prostředí je definované implementací (najdete v části [části 4.1](../../parallel/openmp/4-1-omp-schedule.md) na stránce 48).  
  
     V jazyce Visual C++, typ plánu je `static` s žádné velikost bloku.  
  
-   `OMP_NUM_THREADS`proměnné prostředí: Pokud není zadaná žádná hodnota pro `OMP_NUM_THREADS` proměnné prostředí, nebo pokud zadaná hodnota není celé kladné číslo, nebo pokud je hodnota větší než maximální počet vláken, může podporovat systému, je počet vláken používaných definované implementací (viz [části 4.2](../../parallel/openmp/4-2-omp-num-threads.md) na stránce 48).  
  
     V jazyce Visual C++ Pokud zadaná hodnota je nulová nebo méně, počet vláken, se rovná počtu procesorů.  Pokud je hodnota vyšší než 64, počet vláken je 64.  
  
-   `OMP_DYNAMIC`proměnné prostředí: výchozí hodnota je definované implementací (najdete v části [části 4.3](../../parallel/openmp/4-3-omp-dynamic.md) na stránce 49).  
  
     V jazyce Visual C++, výchozí hodnota je `FALSE`.