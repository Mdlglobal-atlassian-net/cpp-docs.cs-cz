---
title: A.10   Nastavení sekvenčního řazení
ms.date: 11/04/2016
ms.assetid: 5c65a9b1-0fc5-4cad-a5a9-9ce10b25d25c
ms.openlocfilehash: 4e3a146e1bca988f46cf7a7ee504644f96dab67e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575250"
---
# <a name="a10---specifying-sequential-ordering"></a>A.10   Nastavení sekvenčního řazení

Seřazené oddíly ([části 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) na stránce 22) jsou užitečné pro sekvenční řazení výstup z práce, která se provádí současně. Následující program vytiskne indexy v postupném pořadí:

```
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```