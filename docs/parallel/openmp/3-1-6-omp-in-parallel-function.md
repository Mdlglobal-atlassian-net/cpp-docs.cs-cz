---
title: 3.1.6 omp_in_parallel – funkce
ms.date: 11/04/2016
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
ms.openlocfilehash: 2f251cb994771278c7f4e3f50f01e02126f6f88d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482040"
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel – funkce

**Omp_in_parallel** funkce vrátí nenulovou hodnotu, pokud je volána v rámci dynamický rozsah paralelní oblasti paralelně prováděných; v opačném případě vrátí hodnotu 0. Formát je následujícím způsobem:

```
#include <omp.h>
int omp_in_parallel(void);
```

Tato funkce vrátí nenulovou hodnotu při volání z v rámci oblasti spouští paralelně, včetně vnořených oblastí, které se serializují.