---
title: "Určení pevný počet vláken A.11 | Microsoft Docs"
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
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 72c8aca2b90f021771ba9f9fc8a86d784ffe24a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="a11---specifying-a-fixed-number-of-threads"></a>A.11   Určení pevného počtu vláken
Některé programy spoléhají na pevnou, prespecified počet vláken správně spustit.  Protože výchozí nastavení pro dynamické přizpůsobení počet vláken je definované implementací, takové programy můžete vypnout funkce dynamické vláken a nastavte počet vláken explicitně zajistit přenositelnost. Následující příklad ukazuje, jak to provést pomocí `omp_set_dynamic` ([části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39), a `omp_set_num_threads` ([bod 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stránce 36):  
  
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
  
 V tomto příkladu se program spustí správně pouze v případě, že je provedený 16 vláken. Pokud implementace není schopný zajistit podporu 16 vláken, chování tohoto příkladu je definované implementací.  
  
 Všimněte si, že počet vláken provádění paralelní oblast zůstane konstantní během paralelní oblast, bez ohledu na nastavení dynamické vláken. Mechanismus dynamické vláken určuje počet vláken používaných na začátku oblasti paralelní a udržuje ho konstantní po dobu trvání oblasti.