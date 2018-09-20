---
title: A.3 použití paralelních oblastí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 575216a1-960a-47f7-9c82-7f660291fcfe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82bc1655584af300cb2d36a62250595839d74551
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413078"
---
# <a name="a3---using-parallel-regions"></a>A.3   Použití paralelních oblastí

`parallel` – Direktiva ([části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8) lze použít v paralelních programů hrubý intervalem. V následujícím příkladu, každé vlákno v paralelní oblasti určuje, jaká část globální pole `x` pracovat na, závisí na počtu vláken:

```
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```