---
title: "Paralelní provádění jednoduché smyčky A.1 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d2c6cfe794b9d7f50d7e12b8d2f444628ec6d79f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1   Spuštění jednoduché paralelní smyčky
Následující příklad ukazuje, jak učinit paralelní jednoduché smyčky pomocí `parallel for` – direktiva ([části 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) na stránce 16). Proměnné iterace smyčky je soukromé ve výchozím nastavení, takže není nutné explicitně zadat v klauzuli privátní.  
  
```  
#pragma omp parallel for  
    for (i=1; i<n; i++)  
        b[i] = (a[i] + a[i-1]) / 2.0;  
```