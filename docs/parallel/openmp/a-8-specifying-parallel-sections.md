---
title: A.8   Určení paralelních oddílů
ms.date: 11/04/2016
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
ms.openlocfilehash: 81eaed920e77b23052ac58c2d0e18fee83c00565
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461435"
---
# <a name="a8---specifying-parallel-sections"></a>A.8   Určení paralelních oddílů

V následujícím příkladu (pro [části 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) na stránce 14) funkce *xaxis*, *osa yrozsah*, a *zaxis* mohou být provedeny souběžně. První `section` direktiva je volitelné.  Všimněte si, že všechny `section` direktivy, musí se zobrazit v lexikálním rozsahu `parallel sections` vytvořit.

```
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```