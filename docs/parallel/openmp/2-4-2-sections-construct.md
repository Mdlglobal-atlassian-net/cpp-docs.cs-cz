---
title: 2.4.2 sections – konstrukce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35ae940e37b40cbb9c883c4d7d6bca7b0fa65520
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410543"
---
# <a name="242-sections-construct"></a>2.4.2 sections – konstrukce

**Oddíly** – direktiva určuje noniterative konstruktoru work-sharing, který určuje sadu konstrukce, které jsou k rozdělení mezi vlákny v týmu. Každá část je spuštěna jednou vláknem v týmu. Syntaxe **oddíly** direktivy je následující:

```
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

V klauzuli je jedním z následujících akcí:

**privátní (** *seznamu proměnné* **)**

**firstprivate (** *seznamu proměnné* **)**

**lastprivate (** *seznamu proměnné* **)**

**snížení (** *operátor* **:***seznamu proměnné* **)** 

**nowait**

Každá část předchází **části** směrnice, i když **části** – direktiva je nepovinné pro první část. **Části** direktivy musí být použit v lexikálním rozsahu **oddíly** směrnice. Na konci je implicitní bariéry **oddíly** sestavit, pokud **nowait** je zadán.

Omezení **oddíly** směrnice jsou následující:

- A **části** – direktiva nesmí objevit mimo lexikální rozsah **oddíly** směrnice.

- Pouze jeden **nowait** klauzule se může objevit v **oddíly** směrnice.

## <a name="cross-references"></a>Křížové odkazy:

- **privátní**, **firstprivate**, **lastprivate**, a **snížení** klauzule, naleznete v tématu [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.