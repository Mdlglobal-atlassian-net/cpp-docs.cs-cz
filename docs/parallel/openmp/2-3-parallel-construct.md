---
title: 2.3 parallel – konstrukce
ms.date: 11/04/2016
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
ms.openlocfilehash: 6ee7539af05bef1fdca117d806900f2f5a9c0d7f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494672"
---
# <a name="23-parallel-construct"></a>2.3 parallel – konstrukce

Následující direktiva definuje paralelní oblasti, která je oblast programu, který má být vykonán paralelně několik vláken. Toto je základní koncept, který se spustí paralelní zpracování.

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

**num_threads(** *integer-expression* **)**

Pokud vlákno narazí paralelní konstrukce, tým vláken se vytvoří, pokud je splněna jedna z následujících případech:

- Ne **Pokud** je přítomna klauzule.

- **Pokud** výraz vyhodnocen nenulovou hodnotu.

Toto vlákno se stane hlavní vlákno tým s počtem vláken 0, a všechna vlákna v týmu, včetně hlavní vlákno paralelně spustit oblast. Pokud hodnota **Pokud** výraz je nula, je serializován v oblasti.

Pokud chcete zjistit počet vláken, které jsou požadovány, tato pravidla se budou považovat za v pořadí. První pravidlo, jehož podmínka je splněna se použijí:

1. Pokud **num_threads** je přítomna klauzule, pak hodnota celočíselný výraz je počet vláken požadovaný.

1. Pokud **omp_set_num_threads –** byla volána funkce knihovny, pak je počet vláken požadované hodnoty argumentu v nedávno provedených volání.

1. Pokud proměnná prostředí **OMP_NUM_THREADS** je definována hodnota této proměnné prostředí je počet vláken požadovaný.

1. Pokud žádná z výše uvedených metod používaly počet vláken požadované je definován implementací.

Pokud **num_threads** je přítomna klauzule pak nahrazuje počet vláken požadoval **omp_set_num_threads –** funkce knihovny nebo **OMP_NUM_THREADS** proměnné prostředí pouze pro paralelní oblasti, které bylo použito. Následné paralelních oblastí nejsou vliv.

Počet vláken, které jsou spouštěny paralelní oblasti se také závisí na tom, zda je povolena dynamické úpravy počtu vláken. Pokud je zakázané dynamické úpravy, požadovaný počet vláken spustí paralelní oblasti. Pokud je povolené dynamické úpravy požadovaný počet vláken je maximální počet vláken, která se dá provádět paralelní oblasti.

Pokud při dynamické úpravy počtu vláken je zakázané, a číslo, které můžete zadat za běhu systému překračuje počet vláken, které jsou požadované pro paralelní oblasti je zjištěna paralelní oblasti, je chování programu definované implementací. Implementace může například přerušit provádění programu, nebo ji může serializovat paralelní oblasti.

**Omp_set_dynamic –** funkce knihovny a **OMP_DYNAMIC** proměnnou prostředí je možné povolit nebo zakázat dynamické úpravy počtu vláken.

Počet fyzických procesorů ve skutečnosti hostování vlákna v daném okamžiku je definován implementací. Po vytvoření počet vláken v týmu konstantní po dobu trvání tohoto paralelní oblasti. Lze jej změnit buď explicitně uživatelem, nebo automaticky za běhu systému z jedné paralelní oblasti do jiného.

Příkazy obsažené v dynamický rozsah paralelní oblasti jsou spouštěny jednotlivými vlákny a každé vlákno může spustit cestu příkazy, které se liší od jiných vláken. Došlo k mimo lexikální rozsah paralelní oblasti direktivy jsou označovány jako osamocený direktivy.

Není k dispozici implicitní barrier na konci paralelní oblasti. Pouze hlavní vlákno tým pokračuje v provádění na konci paralelní oblasti.

Pokud vlákno v tým provádí paralelní oblasti zaznamená jiné paralelní konstrukce, vytvoří nový tým a stane se hlavní tento nový tým. Ve výchozím nastavení jsou serializovat vnořený paralelních oblastí. Ve výchozím nastavení, proto vnořené paralelní oblasti provádí týmem, který se skládá z jednoho vlákna. Výchozí chování může změnit pomocí funkce knihovny prostředí runtime **omp_set_nested –** nebo proměnnou prostředí **OMP_NESTED**. Počet vláken v týmu, které jsou spuštěny paralelní vnořené oblasti je však definován implementací.

Omezení **paralelní** směrnice jsou následující:

- Maximálně jeden **Pokud** klauzule se může objevit v direktivě.

- Neurčené Určuje, zda všechny na straně účinky uvnitř if je výraz nebo **num_threads** dojde k výraz.

- A **throw** provést uvnitř paralelní oblasti musíte zajistit, aby v provádění pokračovat v rámci dynamický rozsah stejné strukturovaný blok, a musí být zachycena ve stejném vlákně, které vyvolalo výjimku.

- Pouze jeden **num_threads** klauzule se může objevit v direktivě. **Num_threads** výraz je vyhodnocen mimo kontext paralelní oblasti a musí být kladná celočíselná hodnota.

- Pořadí vyhodnocování **Pokud** a **num_threads** není zadána klauzule.

## <a name="cross-references"></a>Křížové odkazy:

- **privátní**, **firstprivate**, **výchozí**, **sdílené**, **copyin**, a **snížení**klauzule, naleznete v tématu [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.

- **OMP_NUM_THREADS** proměnnou prostředí [části 4.2](../../parallel/openmp/4-2-omp-num-threads.md) na stránce 48.

- **omp_set_dynamic –** funkce knihovny, najdete v článku [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.

- **OMP_DYNAMIC** proměnné, viz prostředí [části 4.3](../../parallel/openmp/4-3-omp-dynamic.md) na stránce 49.

- **omp_set_nested –** funkce naleznete v tématu [části 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stránce 40.

- **OMP_NESTED** proměnné, viz prostředí [části 4.4](../../parallel/openmp/4-4-omp-nested.md) na stránce 49.

- **omp_set_num_threads –** funkce knihovny, najdete v článku [části 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stránce 36.