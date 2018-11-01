---
title: 3.2.1 omp_init_lock a omp_init_nest_lock – funkce
ms.date: 11/04/2016
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
ms.openlocfilehash: 2d15aacb5e6743d18150fb45bea85b7ca22a401f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472773"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock a omp_init_nest_lock – funkce

Tyto funkce jsou pouze prostředkem inicializaci zámek. Každá funkce inicializuje zámek spojené s parametrem *Zámek* pro použití v následných volání. Formát je následujícím způsobem:

```
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Počáteční stav se odemkne (to znamená, že žádné vlákno vlastníkem zámku). Pro zámek, vnořitelných počáteční počet vnoření je nula. Jde volat některý z těchto rutin s proměnnou zámek, který už je inicializovaný nedodržující předpisy.