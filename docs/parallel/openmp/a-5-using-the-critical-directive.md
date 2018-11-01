---
title: A.5   Použití direktivy critical
ms.date: 11/04/2016
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
ms.openlocfilehash: 82497d63acc057fbbcf26f585e42fc8611c08ec4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545095"
---
# <a name="a5---using-the-critical-directive"></a>A.5   Použití direktivy critical

Následující příklad obsahuje několik `critical` direktivy ([části 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) na stránce 18). Tento příklad znázorňuje modelu služby Řízení front, ve kterém je úkol vyřazených z fronty a pracovali. Pro ochranu proti více vláken vyřazování z fronty, stejný úkol, zrušení fronty operace musí být v `critical` oddílu. Vzhledem k tomu, že dvě fronty v tomto příkladu jsou nezávislé, jsou chráněné službou `critical` direktivy s různými názvy, *xaxis* a *osa yrozsah*.

```
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```