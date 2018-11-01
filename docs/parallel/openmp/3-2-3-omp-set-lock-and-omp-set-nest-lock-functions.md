---
title: 3.2.3 omp_set_lock a omp_set_nest_lock – funkce
ms.date: 11/04/2016
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
ms.openlocfilehash: 8efc1f844be2d1b8cf9b15242758914edd0fca14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617656"
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock a omp_set_nest_lock – funkce

Každá z těchto funkcí blokuje vlákno provádění funkce, dokud se zadaný zámek je k dispozici a pak nastaví zámek. Jednoduchým zámkem je k dispozici, pokud je odemknuté. Vnořitelných zámek je k dispozici, pokud je odemčený, nebo pokud je již vlastněn vlákno provádění funkce. Formát je následujícím způsobem:

```
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Pro jednoduchým zámkem, že argument `omp_set_lock` funkce musí ukazovat na proměnnou inicializované zámku. Vlákna, které spouští funkci uděleno vlastnictví zámku.

Pro zámkem, že argument `omp_set_nest_lock` funkce musí ukazovat na proměnnou inicializované zámku. Je zvýšen počet vnoření a vlákna je udělen nebo zůstane vlastnictví zámku.