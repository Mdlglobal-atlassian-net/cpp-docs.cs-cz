---
title: A.27 použití polí proměnné délky C99 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51fda970f78592c8a4e10d17d370e9c78f0ea493
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405889"
---
# <a name="a27---use-of-c99-variable-length-arrays"></a>A.27   Použití polí proměnné délky C99

Následující příklad ukazuje způsob použití polí proměnné délky (VLAs) C99 v `firstprivate` – direktiva ([části 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) na stránce 26).

> [!NOTE]
>  Pole s proměnnou délkou se momentálně nepodporují v jazyce Visual C++.

```
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```