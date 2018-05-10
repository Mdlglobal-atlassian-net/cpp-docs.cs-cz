---
title: Příklady A.23 seřazené – direktiva | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37cc4ea9db8cbd1a7bf095e2bde0ae482053a584
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23   Příklady použití direktivy ordered
Je možné, že více seřazené oddílů s `for` zadaný `ordered` klauzule. V prvním příkladu je nekompatibilní, protože rozhraní API určuje následující:  
  
 "Iterace smyčky pomocí `for` konstrukce nesmí provést stejný `ordered` direktivy více než jednou ale nesmí spuštění více než jeden `ordered` – direktiva." (Viz [část 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) na stránce 22)  
  
 V tomto příkladu nekompatibilních spuštění všech iterací 2 seřazené částech:  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
}  
```  
  
 Ukazuje následující příklad kompatibilní `for` s více než jeden seřazené části:  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    if (i <= 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
    (i > 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
}  
```