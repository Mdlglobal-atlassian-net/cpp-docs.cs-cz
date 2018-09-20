---
title: 3.1.3 omp_get_max_threads – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c439dc0203fa3435c62e9669da40b5b092556492
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400819"
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