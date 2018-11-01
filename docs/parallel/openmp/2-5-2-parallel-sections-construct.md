---
title: 2.5.2 parallel sections – konstrukce
ms.date: 11/04/2016
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
ms.openlocfilehash: 1b74dacb9730a14364d7202918ae195cbf691955
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533663"
---
# <a name="252-parallel-sections-construct"></a>2.5.2 parallel sections – konstrukce

**Parallel sections –** – direktiva poskytuje místní formulář pro zadávání **paralelní** oblasti, který obsahuje pouze jedinou **oddíly** – direktiva. Sémantika je shodné s explicitním zadáním **paralelní** směrnice okamžitě následovat **oddíly** – direktiva. Syntaxe **parallel sections –** direktivy je následující:

```
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*Klauzule* může být jedna z klauzule přijal **paralelní** a **oddíly** direktivy, s výjimkou **nowait** klauzuli.

## <a name="cross-references"></a>Křížové odkazy:

- **paralelní** direktiv, viz [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.

- **oddíly** direktiv, viz [části 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) na stránce 14.