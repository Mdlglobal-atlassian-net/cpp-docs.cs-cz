---
title: A.15   Určení počtu použitých vláken
ms.date: 11/04/2016
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
ms.openlocfilehash: bd5e897eeab35ec73c061d2ae02a4b85772e1255
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525828"
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15   Určení počtu použitých vláken

Podívejte se na následující příklad nesprávné (pro [části 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37):

```
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

`omp_get_num_threads()` Volání vrátí hodnotu 1 v sériového portu části kódu, takže *np* bude vždy rovné 1 v předchozím příkladu. Pokud chcete zjistit počet vláken, která se nasadí pro paralelní oblasti, třeba volání uvnitř paralelní oblasti.

Následující příklad ukazuje, jak přepsat tento program bez zahrnutí dotaz na počet vláken:

```
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```