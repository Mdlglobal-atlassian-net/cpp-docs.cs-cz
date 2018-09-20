---
title: A.10 nastavení sekvenčního řazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5c65a9b1-0fc5-4cad-a5a9-9ce10b25d25c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29f2089760e9aef6f9e992c5725eab12b7be3b20
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432227"
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