---
title: 3.2.5 omp_test_lock a omp_test_nest_lock – funkce
ms.date: 11/04/2016
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
ms.openlocfilehash: e8e03699f807f23f139075560592d8846467f2c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512747"
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock a omp_test_nest_lock – funkce

Tyto funkce pokus o nastavení zámku ale neblokují provádění vlákna. Formát je následujícím způsobem:

```
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

Argument musí ukazovat na proměnnou inicializované zámku. Tyto funkce se pokusí nastavit zámek stejným způsobem jako `omp_set_lock` a `omp_set_nest_lock`, s tím rozdílem, že nebudou blokovat spuštění vlákna.

Pro jednoduché Zámek `omp_test_lock` funkce vrací nenulovou hodnotu, pokud je úspěšně nastavené uzamčení; v opačném případě vrátí 0.

Pro zámek, vnořitelných `omp_test_nest_lock` funkce vrací nový počet vnoření, pokud je úspěšně nastavené uzamčení; v opačném případě vrátí 0.