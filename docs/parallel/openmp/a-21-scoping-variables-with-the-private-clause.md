---
title: A.21   Rozsah platnosti proměnných s klauzulí private
ms.date: 11/04/2016
ms.assetid: 7cdb4a7f-af24-44ac-9d33-e43840bc8f3d
ms.openlocfilehash: 4217bcc3911ded88b9385695c8c0ac851fceae9e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616124"
---
# <a name="a21---scoping-variables-with-the-private-clause"></a>A.21   Rozsah platnosti proměnných s klauzulí private

Hodnoty `i` a `j` v následujícím příkladu jsou definovaná na ukončení paralelní oblasti:

```
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

Další informace o `private` klauzule, naleznete v tématu [části 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stránce 25.