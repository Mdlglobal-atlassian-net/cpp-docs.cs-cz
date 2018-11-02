---
title: A.6   Použití klauzule lastprivate
ms.date: 11/04/2016
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
ms.openlocfilehash: 7d5ba1413827590b7fb3afa0847b9aa1da3c41e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579801"
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6   Použití klauzule lastprivate

Někdy správné spuštění závisí na hodnotě, který proměnné přiřazuje poslední iteraci smyčky. Takové programy musí uvést všechny tyto proměnné jako argumenty `lastprivate` – klauzule ([části 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) na stránce 27) tak, že hodnoty proměnné jsou stejné jako při provedení smyčky je postupně.

```
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

V předchozím příkladu, hodnota `i` na konci paralelní oblast vyrovná `n-1`, jako v případě sekvenční.