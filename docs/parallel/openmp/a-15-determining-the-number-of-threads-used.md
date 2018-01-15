---
title: "Určení počet vláken používaných A.15 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e8b7fb8cf6218863287d582a097cb43b399cff07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15   Určení počtu použitých vláken
Podívejte se na následující příklad nesprávné (pro [bodu 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37):  
  
```  
np = omp_get_num_threads(); // misplaced   
#pragma omp parallel for schedule(static)  
    for (i=0; i<np; i++)  
        work(i);  
```  
  
 `omp_get_num_threads()` Volání vrátí hodnotu 1 v části sériové kódu, takže *np* bude vždy rovná 1 v předchozím příkladu. Pokud chcete určit počet vláken, které se nasadí pro paralelní oblast, musí být volání uvnitř paralelní oblast.  
  
 Následující příklad ukazuje, jak přepsání tento program bez zahrnutí dotaz na počet vláken:  
  
```  
#pragma omp parallel private(i)  
{  
    i = omp_get_thread_num();  
    work(i);  
}  
```