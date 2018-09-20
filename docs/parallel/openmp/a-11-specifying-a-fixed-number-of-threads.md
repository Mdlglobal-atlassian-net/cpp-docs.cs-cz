---
title: A.11 určení pevného počtu vláken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 892140425dc9f7083c606fce3ffe671a107a65ca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422984"
---
# <a name="a11---specifying-a-fixed-number-of-threads"></a>A.11   Určení pevného počtu vláken

Některé programy spoléhají na pevný, prespecified počet vláken se správně spustit.  Vzhledem k tomu, že výchozí nastavení pro dynamické úpravy počtu vláken, je definováno implementací, těchto programů můžete vypnout funkci dynamického vláken a nastavit počet vláken explicitně pro zajištění přenositelnosti. Následující příklad ukazuje, jak to udělat pomocí `omp_set_dynamic` ([části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39), a `omp_set_num_threads` ([části 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stránce 36):

```
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

V tomto příkladu se program spustí správně pouze v případě, že se provede 16 vlákny. Pokud implementace není schopný zajistit podporu 16 vlákna, chování v tomto příkladu je definován implementací.

Všimněte si, že během paralelní oblasti, bez ohledu na nastavení dynamické vlákna konstantní počet vláken v paralelní oblasti. Mechanismus dynamické vlákna určuje počet vláken na začátku paralelní oblasti a zachová konstantní po dobu trvání oblast.