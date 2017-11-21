---
title: "A.4 pomocí nowait klauzule | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d3de2111-05ea-4ee3-a66c-57bd988712af
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eda3892f843535edf5778e569c025eb00a19e666
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="a4---using-the-nowait-clause"></a>A.4   Použití klauzule nowait
Pokud existují více nezávislých smyčky v rámci paralelní oblasti, můžete použít `nowait` – klauzule ([části 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stránce 11) předejdete předpokládané bariéry na konci `for` – direktiva, následujícím způsobem:  
  
```  
#pragma omp parallel  
{  
    #pragma omp for nowait  
        for (i=1; i<n; i++)  
             b[i] = (a[i] + a[i-1]) / 2.0;  
    #pragma omp for nowait  
        for (i=0; i<m; i++)  
            y[i] = sqrt(z[i]);  
}  
```