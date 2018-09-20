---
title: 2.5.1 parallel for – konstrukce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfff3b0c17dd098b5d802af61a7ca1f81cb02845
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373958"
---
# <a name="251-parallel-for-construct"></a>2.5.1 parallel for – konstrukce

**Paralelní pro** – direktiva je zkratka pro **paralelní** oblast, která obsahuje pouze jeden **pro** směrnice. Syntaxe **paralelní pro** direktivy je následující:

```
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Tato direktiva umožňuje všechny klauzule z **paralelní** směrnice a **pro** direktiv, s výjimkou `nowait` klauzule identické význam a omezení. Sémantika je shodné s explicitním zadáním **paralelní** směrnice okamžitě následovat **pro** – direktiva.

## <a name="cross-references"></a>Křížové odkazy:

- **paralelní** direktiv, viz [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.

- **pro** direktiv, viz [části 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stránce 11.

- Klauzule atributů pro data, najdete v článku [2.7.2 klauzule atributů pro sdílení dat](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.