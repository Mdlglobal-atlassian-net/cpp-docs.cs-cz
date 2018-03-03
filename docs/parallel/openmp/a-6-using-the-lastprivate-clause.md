---
title: "A.6 pomocí lastprivate klauzule | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1744787e1dfb90fa9af93db5dba4eecd600b4334
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6   Použití klauzule lastprivate
Někdy správné provedení závisí na základě hodnoty, který proměnné přiřazuje poslední iteraci smyčky. Takové programy musí seznam všech těchto proměnných jako argumenty pro `lastprivate` – klauzule ([části 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) na stránce 27) tak, aby hodnoty proměnných jsou stejné jako při postupně smyčky.  
  
```  
#pragma omp parallel  
{  
   #pragma omp for lastprivate(i)  
      for (i=0; i<n-1; i++)  
         a[i] = b[i] + b[i+1];  
}  
a[i]=b[i];  
```  
  
 V předchozím příkladu, hodnota `i` na konci oblasti paralelní bude rovnat `n-1`, jako v případě sekvenční.