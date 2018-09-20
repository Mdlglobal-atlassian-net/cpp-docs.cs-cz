---
title: 3.1.1 omp_set_num_threads – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85f7ff733583e531b449caf2039817b71165da52
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426793"
---
# <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads – funkce

`omp_set_num_threads` Funkce nastaví výchozí počet vláken pro následné paralelních oblastí, které není zadán `num_threads` klauzuli. Formát je následujícím způsobem:

```
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Hodnota parametru *num_threads* musí být kladné celé číslo. Jeho dopad závisí na tom, zda je povolena dynamické úpravy počtu vláken. Pro komplexní sadu pravidel o interakci mezi `omp_set_num_threads` funkce a dynamické úpravy vláken, najdete v části 2.3 na stránce 8.

Tato funkce má důsledky je popsáno výše, při volání z část programu, kde `omp_in_parallel` vrátí funkce hodnotu nula. Pokud je volána z část programu, kde `omp_in_parallel` funkce vrátí nenulovou hodnotu, nedefinované chování této funkce.

Toto volání má vyšší prioritu než `OMP_NUM_THREADS` proměnné prostředí. Výchozí hodnota pro počet vláken, které mohou být stanoveny voláním `omp_set_num_threads` nebo nastavením `OMP_NUM_THREADS` proměnné prostředí, můžete explicitně přepsat v rámci jednoho **paralelní** direktiv tak, že zadáte `num_threads` klauzuli.

## <a name="cross-references"></a>Křížové odkazy:

- `omp_set_dynamic` Funkce, najdete v článku [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.

- `omp_get_dynamic` Funkce, najdete v článku [části 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) na stránce 40.

- `OMP_NUM_THREADS` Proměnná, viz prostředí [části 4.2](../../parallel/openmp/4-2-omp-num-threads.md) na stránce 48 a 2.3 části na stránce 8.

- `num_threads` klauzule, naleznete v tématu [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8