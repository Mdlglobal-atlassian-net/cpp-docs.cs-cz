---
title: "Příklady A.23 seřazené – direktiva | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 83d77bb4f064a7ee69b013b36de919b57486b3e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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