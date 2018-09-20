---
title: A.23 příklady použití direktivy seřazený směrnice | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec609a77e9bdc7cbdbb0822dfde0a88110ce0244
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405967"
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