---
title: 3.3.1 omp_get_wtime – funkce
ms.date: 11/04/2016
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
ms.openlocfilehash: 544a1bc9a613a2888cb7c5e68e54fdfae1b1c333
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460564"
---
# <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime – funkce

`omp_get_wtime` Funkce vrátí dvojité přesnosti s plovoucí desetinnou čárkou hodnota bodu rovnou skutečný uplynulý čas v sekundách, protože některé "čas v minulosti".  Skutečný "čas v minulosti" je volitelný, ale je zaručeno, že nelze změnit během provádění programu aplikace. Formát je následujícím způsobem:

```
#include <omp.h>
double omp_get_wtime(void);
```

Předpokládá se, že funkce se použije k měření uplynulého času, jak je znázorněno v následujícím příkladu:

```
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Vrátí časy jsou "vlákno times" ve kterém je určený, že nemusí být globálně konzistentní v rámci všech vláken součástí aplikace.