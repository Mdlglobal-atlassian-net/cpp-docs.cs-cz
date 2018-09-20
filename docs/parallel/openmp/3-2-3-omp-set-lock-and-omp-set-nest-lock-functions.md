---
title: 3.2.3 omp_set_lock a omp_set_nest_lock – Functions | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 792b95baef2821bb693d9a90fc228d2b0c508e1f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420358"
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