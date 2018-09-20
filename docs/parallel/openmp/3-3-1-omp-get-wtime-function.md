---
title: 3.3.1 omp_get_wtime – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec022e9c7e27c848ef535481993dd18dc45f695
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430764"
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