---
title: Paralelní provádění jednoduché smyčky A.1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b2fbac6ce31d2dbc56a4ef6d9fe87c14d5ee16
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686123"
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1   Spuštění jednoduché paralelní smyčky
Následující příklad ukazuje, jak učinit paralelní jednoduché smyčky pomocí `parallel for` – direktiva ([části 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) na stránce 16). Proměnné iterace smyčky je soukromé ve výchozím nastavení, takže není nutné explicitně zadat v klauzuli privátní.  
  
```  
#pragma omp parallel for  
    for (i=1; i<n; i++)  
        b[i] = (a[i] + a[i-1]) / 2.0;  
```