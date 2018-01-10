---
title: "2.3 parallel – konstrukce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 89167547085682a81cc1d281f4f32ab55022d27c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="23-parallel-construct"></a>2.3 parallel – konstrukce
Následující direktiva definuje paralelní oblasti, která je oblasti program, který se má provádět více podprocesů paralelně. Toto je základní koncept, která se spouští paralelní provádění.  
  
```  
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block  
```  
  
 *Klauzule* je jedním z následujících akcí:  
  
 **Pokud (** *skalární výraz* **)**  
  
 **privátní (** *seznamu proměnné* **)**  
  
 **firstprivate (** *seznamu proměnné* **)**  
  
 **Výchozí (sdílené &#124; none)**  
  
 **sdílené (** *seznamu proměnné* **)**  
  
 **copyin (** *seznamu proměnné* **)**  
  
 **snížení (** *operátor* **:***seznamu proměnné* **)**   
  
 **num_threads (** *celočíselný výraz* **)**  
  
 Když vlákno dojde paralelní konstrukce, tým vláken je vytvořen, pokud platí jedna z následujících případech:  
  
-   Ne **Pokud** klauzule je k dispozici.  
  
-   **Pokud** výraz vyhodnocen jako nenulová hodnota.  
  
 Tento přístup z více vláken stane hlavní vlákno týmu s číslem vlákna 0, a všechna vlákna v týmu, včetně hlavní vlákno paralelně provádět oblasti. Pokud hodnota **Pokud** výraz rovná nule, je serializováno oblasti.  
  
 Pokud chcete určit počet vláken, které jsou požadovány, bude považovat za následující pravidla v pořadí. Bude použito první pravidlo je splněna podmínka, jejíž:  
  
1.  Pokud **num_threads** klauzule je k dispozici, pak hodnota celočíselný výraz je počet vláken požadovaný.  
  
2.  Pokud **omp_set_num_threads –** byla volána funkce knihovny, pak hodnota argumentu v nedávno provedených volání je počet vláken požadovaný.  
  
3.  Pokud proměnná prostředí **OMP_NUM_THREADS** je definován, je počet vláken požadovanou hodnotu této proměnné prostředí.  
  
4.  Pokud žádná z výše uvedených metod používaly počet vláken požadovaný je definované implementací.  
  
 Pokud **num_threads** nachází klauzule pak nahrazuje počet vláken požadoval **omp_set_num_threads –** funkce knihovny nebo **OMP_NUM_THREADS** proměnné prostředí pouze pro paralelní oblast bylo použito. Následné paralelní oblasti nemá vliv ho.  
  
 Počet vláken, které se spouští paralelní oblasti se také závisí na tom, zda je povolena dynamické přizpůsobení počet vláken. Pokud je zakázána dynamické přizpůsobení, požadovaný počet vláken, spustí paralelní oblast. Pokud je povolené dynamické přizpůsobení požadovaný počet vláken, je maximální počet vláken, které může provést paralelní oblast.  
  
 Pokud paralelní oblast je došlo při dynamické přizpůsobení počet vláken je zakázané a počet vláken, které jsou požadované pro paralelní oblast překračuje číslo, které můžete zadat běhu systému, je chování programu implementace definované. Implementace může například přerušení spuštění programu, nebo ho může serializovat paralelní oblast.  
  
 **Omp_set_dynamic –** funkce knihovny a **OMP_DYNAMIC** proměnnou prostředí slouží k povolení a zákaz dynamické přizpůsobení počet vláken.  
  
 Počet fyzických procesorů ve skutečnosti hostování vláken v každém okamžiku je definované implementací. Po vytvoření zůstává po dobu trvání této paralelní oblasti konstantní počet vláken v týmu. Lze změnit buď explicitně uživatelem, nebo automaticky v běhu systému z jedné oblasti paralelní do jiného.  
  
 Příkazy obsažené v dynamické rozsah paralelní oblasti jsou spouštěny jednotlivými vlákny a každý podproces může provést cesta příkazy, které se liší od jiných vláken. Direktivy došlo mimo lexikální rozsah paralelní oblasti jsou označovány jako osamocený direktivy.  
  
 Není předpokládané bariéry na konci paralelní oblast. Pouze hlavní vlákno týmu pokračuje v provádění na konci paralelní oblast.  
  
 Pokud vlákna v týmu provádění paralelní oblast zaznamená jiné paralelní konstrukce, vytvoří nový tým a stává se k hlavnímu serveru tento nový tým. Ve výchozím nastavení se serializují paralelní vnořené oblasti. Ve výchozím nastavení, v důsledku toho je oblast paralelní vnořené provést týmem, který se skládá z jednoho vlákna. Nejspíš se změní výchozí chování můžete použít buď funkci runtime knihovny **omp_set_nested –** nebo proměnná prostředí **OMP_NESTED**. Počet vláken v týmu, které se spouští paralelní vnořené oblast je však definované implementací.  
  
 Omezení **paralelní** – direktiva jsou následující:  
  
-   Maximálně jeden **Pokud** klauzule lze zobrazit na direktivu.  
  
-   Není zadáno, jestli na žádné straně důsledky uvnitř zda výraz nebo **num_threads** výraz dojít.  
  
-   A **throw** provést uvnitř paralelní oblast musí způsobit provádění pokračovat v rámci dynamické rozsah na stejný blok strukturovaných a musí být zachycena ve stejném vlákně, která vrátila výjimku.  
  
-   Jediným **num_threads** klauzule lze zobrazit na direktivu. **Num_threads** výraz vyhodnotí mimo kontext paralelní oblasti a musí být kladné celé číslo.  
  
-   Pořadí vyhodnocení **Pokud** a **num_threads** klauzule není zadáno.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **privátní**, **firstprivate**, **výchozí**, **sdílené**, **copyin**, a **snížení**klauzule, najdete v části [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.  
  
-   **OMP_NUM_THREADS** proměnnou prostředí [části 4.2](../../parallel/openmp/4-2-omp-num-threads.md) na stránce 48.  
  
-   **omp_set_dynamic –** funkce knihovny, najdete v části [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.  
  
-   **OMP_DYNAMIC** proměnné, naleznete v prostředí [části 4.3](../../parallel/openmp/4-3-omp-dynamic.md) na stránce 49.  
  
-   **omp_set_nested –** funkce najdete v tématu [části 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stránce 40.  
  
-   **OMP_NESTED** proměnné, naleznete v prostředí [části 4.4](../../parallel/openmp/4-4-omp-nested.md) na stránce 49.  
  
-   **omp_set_num_threads –** funkce knihovny, najdete v části [bod 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stránce 36.