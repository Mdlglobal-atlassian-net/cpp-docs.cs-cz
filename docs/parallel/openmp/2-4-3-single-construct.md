---
title: 2.4.3 single – konstrukce
ms.date: 11/04/2016
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
ms.openlocfilehash: 7dda98ee83ee08adc29830a9c4ada71a208705fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466362"
---
# <a name="243-single-construct"></a>2.4.3 single – konstrukce

**Jeden** – direktiva určuje konstrukce, která určuje, že přidružené strukturovaný blok provádí pouze jedno vlákno v týmu (ne tedy nutně hlavní vlákno). Syntaxe **jeden** direktivy je následující:

```
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

V klauzuli je jedním z následujících akcí:

**privátní (** *seznamu proměnné* **)**

**firstprivate (** *seznamu proměnné* **)**

**copyprivate (** *seznamu proměnné* **)**

**nowait**

Je implicitní barrier po **jeden** vytvořit, není-li **nowait** není zadána klauzule.

Omezení **jeden** směrnice jsou následující:

- Pouze jeden **nowait** klauzule se může objevit v **jeden** směrnice.

- **Copyprivate** klauzule se nesmí používat s **nowait** klauzuli.

## <a name="cross-references"></a>Křížové odkazy:

- **privátní**, **firstprivate**, a **copyprivate** klauzule, naleznete v tématu [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.