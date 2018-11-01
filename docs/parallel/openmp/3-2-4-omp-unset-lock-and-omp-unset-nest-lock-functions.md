---
title: 3.2.4 omp_unset_lock a omp_unset_nest_lock – funkce
ms.date: 11/04/2016
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
ms.openlocfilehash: b0764e3590f8edb3a3e783d9b5493a64be154401
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607863"
---
# <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 omp_unset_lock a omp_unset_nest_lock – funkce

Tyto funkce prostředkem uvolnění vlastnictví zámku. Formát je následujícím způsobem:

```
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

Argument pro každý z těchto funkcí musí ukazovat na proměnnou inicializované zámek vlastněný vláknem provádění funkce. Pokud vlákno není vlastníkem tohoto uzamknout, není chování definováno.

Pro jednoduché Zámek `omp_unset_lock` funkce uvolní vlákno provádění funkce z vlastnictví zámku.

Pro zámek, vnořitelných `omp_unset_nest_lock` funkce sníží počet vnoření a verzí vlákno provádění funkce z vlastnictví zámku, pokud výsledný počet je nula.