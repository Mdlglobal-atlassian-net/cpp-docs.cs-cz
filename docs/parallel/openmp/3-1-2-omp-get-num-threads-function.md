---
title: 3.1.2 omp_get_num_threads – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 512c09b0cf71a7fd9c7438b6f9cceb9f16126718
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424975"
---
# <a name="312-ompgetnumthreads-function"></a>3.1.2 omp_get_num_threads – funkce

**Omp_get_num_threads** funkce vrátí počet vláken aktuálně tým provádí paralelní oblasti, ve kterém je volána. Formát je následujícím způsobem:

```
#include <omp.h>
int omp_get_num_threads(void);
```

**Num_threads** klauzule **omp_set_num_threads –** funkce a **OMP_NUM_THREADS** proměnnou prostředí řídí počet vláken v týmu.

Pokud počet vláken není nastavený explicitně uživatelem, výchozí hodnota je definován implementací. Tato funkce vytvoří vazbu na nejbližší uzavírající **paralelní** směrnice. Pokud je volána z sériového portu část programu nebo z vnořené paralelní oblasti, která je serializovaná, tato funkce vrátí hodnotu 1.

## <a name="cross-references"></a>Křížové odkazy:

- **OMP_NUM_THREADS** proměnné, viz prostředí [části 4.2](../../parallel/openmp/4-2-omp-num-threads.md) na stránce 48.

- **num_threads** klauzule, naleznete v tématu [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.

- **paralelní** vytvořit, přečtěte si téma [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.