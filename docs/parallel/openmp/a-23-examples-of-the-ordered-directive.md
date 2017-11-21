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
ms.openlocfilehash: b1d6f50eed2c4e89576dd4c17c5a87599bf59e4f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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