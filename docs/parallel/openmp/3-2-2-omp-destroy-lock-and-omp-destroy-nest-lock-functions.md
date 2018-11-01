---
title: 3.2.2 omp_destroy_lock a omp_destroy_nest_lock – funkce
ms.date: 11/04/2016
ms.assetid: d334907d-94f7-4bbf-b20e-41d53484cbff
ms.openlocfilehash: 02f739ab2834db7eca9b051e6659644c39b51e84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666199"
---
# <a name="322-ompdestroylock-and-ompdestroynestlock-functions"></a>3.2.2 omp_destroy_lock a omp_destroy_nest_lock – funkce

Tyto funkce Ujistěte se, že odkazováno na zámek proměnnou *Zámek* není inicializován. Formát je následujícím způsobem:

```
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Jde volat některý z těchto rutin s proměnnou zámku, která je inicializována nebo odemknout nedodržující předpisy.