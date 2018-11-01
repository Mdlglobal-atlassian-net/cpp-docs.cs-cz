---
title: 3.1.4 omp_get_thread_num – funkce
ms.date: 11/04/2016
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
ms.openlocfilehash: eca8522aeab4702be390d98faaf8920f2d732244
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480925"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num – funkce

`omp_get_thread_num` Funkce vrací číslo vlákna, v rámci jeho týmu vlákna provádění funkce. Vlákno číslo leží mezi 0 a **omp_get_num_threads()**-1 (včetně). Hlavní vlákno týmu je vlákno 0.

Formát je následujícím způsobem:

```
#include <omp.h>
int omp_get_thread_num(void);
```

Pokud je volána ze sériového portu oblasti `omp_get_thread_num` vrátí hodnotu 0. Je-li volat v rámci vnořených paralelní oblasti, která je serializovaná, tato funkce vrátí 0.

## <a name="cross-references"></a>Křížové odkazy:

- `omp_get_num_threads` Funkce, najdete v článku [části 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37.