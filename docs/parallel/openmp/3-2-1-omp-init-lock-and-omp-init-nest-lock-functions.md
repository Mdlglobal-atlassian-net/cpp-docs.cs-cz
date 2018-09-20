---
title: 3.2.1 omp_init_lock a omp_init_nest_lock – Functions | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4303eb3ccfcb1c449022a4be32f94b9f91e6e80c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387000"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock a omp_init_nest_lock – funkce

Tyto funkce jsou pouze prostředkem inicializaci zámek. Každá funkce inicializuje zámek spojené s parametrem *Zámek* pro použití v následných volání. Formát je následujícím způsobem:

```
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Počáteční stav se odemkne (to znamená, že žádné vlákno vlastníkem zámku). Pro zámek, vnořitelných počáteční počet vnoření je nula. Jde volat některý z těchto rutin s proměnnou zámek, který už je inicializovaný nedodržující předpisy.