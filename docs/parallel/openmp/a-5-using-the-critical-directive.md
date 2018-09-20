---
title: A.5 použití direktivy critical | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99f9ab513ae1df5a7e1e62cfefcefe404637c063
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444564"
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