---
title: A.27   Použití polí proměnné délky C99
ms.date: 11/04/2016
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
ms.openlocfilehash: 7b2ee74dcd5adedd02e7a9b311c5d3f67203d892
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655296"
---
# <a name="a27---use-of-c99-variable-length-arrays"></a>A.27   Použití polí proměnné délky C99

Následující příklad ukazuje způsob použití polí proměnné délky (VLAs) C99 v `firstprivate` – direktiva ([části 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) na stránce 26).

> [!NOTE]
>  Pole s proměnnou délkou se momentálně nepodporují v jazyce Visual C++.

```
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```