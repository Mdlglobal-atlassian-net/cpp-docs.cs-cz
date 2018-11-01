---
title: 3.1.7 omp_set_dynamic – funkce
ms.date: 11/04/2016
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
ms.openlocfilehash: 641b2ecfdb19aec9387aa299d22a041f25b22929
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492934"
---
# <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic – funkce

**Omp_set_dynamic –** funkce povolí nebo zakáže dynamické úpravy počtu vláken, které jsou k dispozici pro provádění paralelních oblastí. Formát je následujícím způsobem:

```
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Pokud *dynamic_threads* vyhodnotí na nenulovou hodnotu, počet vláken, která se používají k provádění následujících paralelních oblastí může být slev automaticky běhové prostředí tak, aby co nejlépe využívat systémové prostředky. V důsledku toho je počet vláken, které uživatel zadá maximální počet vláken. Počet vláken v týmu provádí paralelní oblasti zůstane pevné po dobu trvání tohoto paralelní oblasti a je ohlášena **omp_get_num_threads** funkce.

Pokud *dynamic_threads* vyhodnotí na hodnotu 0, dynamické úpravy zakázána.

Tato funkce má důsledky je popsáno výše, při volání z část programu, kde **omp_in_parallel** vrátí funkce hodnotu nula. Pokud je volána z část programu, kde **omp_in_parallel** funkce vrátí nenulovou hodnotu, nedefinované chování této funkce.

Volání **omp_set_dynamic –** má vyšší prioritu než **OMP_DYNAMIC** proměnné prostředí.

Výchozí nastavení pro dynamické úpravy vlákna, je definováno implementací. V důsledku toho uživatel kódy, které závisí na konkrétní počet vláken pro správné spuštění by měly explicitně zakázat dynamické vlákna. Implementace se nevyžadují umožňují dynamicky upravit počet vláken, ale jsou nutné k poskytování rozhraní za účelem podpory přenositelnost na všech platformách.

## <a name="cross-references"></a>Křížové odkazy:

- **omp_get_num_threads** funkce naleznete v tématu [části 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37.

- **OMP_DYNAMIC** proměnné, viz prostředí [části 4.3](../../parallel/openmp/4-3-omp-dynamic.md) na stránce 49.

- **omp_in_parallel** funkce naleznete v tématu [části 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) na stránce 38.