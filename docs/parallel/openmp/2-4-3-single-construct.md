---
title: 2.4.3 jednoduché konstrukce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81abf5324c215b9011ecbd774626a213c2eda653
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376496"
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