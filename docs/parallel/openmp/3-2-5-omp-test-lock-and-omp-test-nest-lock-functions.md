---
title: 3.2.5 omp_test_lock a omp_test_nest_lock – Functions | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5349134bf92f407d4b65df9b92e3eebe87c097c1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426143"
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