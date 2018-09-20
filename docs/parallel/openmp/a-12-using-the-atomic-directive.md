---
title: A.12 použití direktivy atomic | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04daed582cfe87f6e4803b30919af3e07037de7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378745"
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