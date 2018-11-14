---
title: 3.1.3 omp_get_max_threads – funkce
ms.date: 11/04/2016
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
ms.openlocfilehash: 3c80bf61d95aa30878e82ed33a24399b4a72ae50
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518448"
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads – funkce

**Omp_get_max_threads –** funkce vrátí celé číslo, které se musí být přinejmenším stejně velká jako počet vláken, která se použije k vytvoření týmu, pokud paralelní oblasti bez **num_threads** – klauzule byly nastat v daném okamžiku v kódu. Formát je následujícím způsobem:

```
#include <omp.h>
int omp_get_max_threads(void);
```

Následující vyjadřuje dolní mez na hodnotě **omp_get_max_threads –**:

```

threads-used-for-next-team
<= omp_get_max_threads
```

Všimněte si, že pokud používá následující paralelní oblasti **num_threads** klauzule požádat o určitý počet vláken, záruka na dolní mez výsledek **omp_get_max_threads –** žádné dlouhé blokování.

**Omp_get_max_threads –** návratové hodnoty funkce je možné dynamicky přidělit dostatečné úložiště pro všechna vlákna v týmu vytvořený v následných paralelní oblasti.

## <a name="cross-references"></a>Křížové odkazy:

- **omp_get_num_threads** funkce naleznete v tématu [části 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37.

- **omp_set_num_threads –** funkce naleznete v tématu [části 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stránce 36.

- **omp_set_dynamic –** funkce naleznete v tématu [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.

- **num_threads** klauzule, naleznete v tématu [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.