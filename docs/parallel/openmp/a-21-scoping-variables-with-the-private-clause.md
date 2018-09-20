---
title: A.21 rozsah platnosti proměnných s klauzulí private | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7cdb4a7f-af24-44ac-9d33-e43840bc8f3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa68f0ebb5857e3f093e1985bd5f20105bb925c1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392785"
---
# <a name="a21---scoping-variables-with-the-private-clause"></a>A.21   Rozsah platnosti proměnných s klauzulí private

Hodnoty `i` a `j` v následujícím příkladu jsou definovaná na ukončení paralelní oblasti:

```
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

Další informace o `private` klauzule, naleznete v tématu [části 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stránce 25.