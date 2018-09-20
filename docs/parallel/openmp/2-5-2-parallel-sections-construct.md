---
title: 2.5.2 parallel sections – konstrukce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 073d0561fe4bfbb96ed88681a077da6fc985c963
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402327"
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