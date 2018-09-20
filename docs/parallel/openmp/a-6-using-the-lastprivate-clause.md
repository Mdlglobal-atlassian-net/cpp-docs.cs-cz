---
title: A.6 použití klauzule lastprivate | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03d18d3aaf5c5d1cbe03282710ae4f4e2bb613f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390575"
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6   Použití klauzule lastprivate

Někdy správné spuštění závisí na hodnotě, který proměnné přiřazuje poslední iteraci smyčky. Takové programy musí uvést všechny tyto proměnné jako argumenty `lastprivate` – klauzule ([části 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) na stránce 27) tak, že hodnoty proměnné jsou stejné jako při provedení smyčky je postupně.

```
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

V předchozím příkladu, hodnota `i` na konci paralelní oblast vyrovná `n-1`, jako v případě sekvenční.