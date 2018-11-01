---
title: 4.2 OMP_NUM_THREADS
ms.date: 11/04/2016
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
ms.openlocfilehash: 88ddfc226b8ae905e026e2f0979e07581d1ae83b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668205"
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

**OMP_NUM_THREADS** proměnné prostředí nastavuje výchozí počet vláken během provádění, pokud toto číslo je explicitně voláním **omp_set_num_threads –** rutina knihovny nebo pomocí explicitní **num_threads** klauzuli **paralelní** směrnice.

Hodnota **OMP_NUM_THREADS** proměnné prostředí musí být kladné celé číslo. Jeho dopad závisí na tom, zda je povolena dynamické úpravy počtu vláken. Pro komplexní sadu pravidel o interakci mezi **OMP_NUM_THREADS** prostředí proměnné a dynamické úpravy vláken, najdete v části 2.3 na stránce 8.

Pokud není zadána žádná hodnota pro **OMP_NUM_THREADS** proměnné prostředí, nebo pokud zadaná hodnota není kladné celé číslo, nebo pokud je hodnota větší než maximální počet vláken může systém podporovat, počet vláken je definováno implementací.

Příklad:

```
setenv OMP_NUM_THREADS 16
```

## <a name="cross-references"></a>Křížové odkazy:

- **num_threads** klauzule, naleznete v tématu [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.

- **omp_set_num_threads –** funkce naleznete v tématu [části 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stránce 36.

- **omp_set_dynamic –** funkce naleznete v tématu [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.