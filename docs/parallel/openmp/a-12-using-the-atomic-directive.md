---
title: A.12   Použití direktivy atomic
ms.date: 11/04/2016
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
ms.openlocfilehash: 0f75b182e2cae11f0e72d5ca1e67f887294e8f69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504431"
---
# <a name="a12---using-the-atomic-directive"></a>A.12   Použití direktivy atomic

V následujícím příkladu se vyhnete konfliktům časování (souběžné aktualizace prvku *x* ve víc vláknech) s použitím `atomic` – direktiva ([části 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md) na stránce 19):

```
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

Výhodou použití `atomic` – direktiva v tomto příkladu je, že umožňuje aktualizace dvě různé prvky x být provedeny souběžně. Pokud `critical` – direktiva ([části 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) na stránce 18) a pak aktualizuje všechny prvky byly použity místo toho *x* by byl proveden sériově (i když není v žádném zaručené pořadí).

Všimněte si, že `atomic` – direktiva se vztahuje pouze na okamžitě následující příkaz jazyka C nebo C++.  V důsledku toho prvky *y* se neaktualizují atomicky v tomto příkladu.