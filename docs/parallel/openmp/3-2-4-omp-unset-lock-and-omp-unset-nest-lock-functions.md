---
title: 3.2.4 omp_unset_lock a omp_unset_nest_lock – Functions | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 426ac0a5ff974e486f70eed2965fdc27d5acc941
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419103"
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