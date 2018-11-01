---
title: A.23   Příklady použití direktivy ordered
ms.date: 11/04/2016
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
ms.openlocfilehash: 2868b771fd57613981f3c6458b48493a1b26eee4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472273"
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23   Příklady použití direktivy ordered

Je možné mít víc seřazený oddíly se `for` zadaný `ordered` klauzuli. První příklad nedodržuje předpisy, protože rozhraní API určuje následující:

"Iterace smyčky s `for` konstrukce nesmí spustit stejný `ordered` direktiv více než jednou a nesmí spuštění více než jedné `ordered` – direktiva." (Viz [části 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) na stránce 22)

V tomto příkladu nedodržující předpisy spuštění všech iterací 2 seřazený oddílů:

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

Následující příklad, který je kompatibilní `for` s více než jednu uspořádanou sekci:

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```