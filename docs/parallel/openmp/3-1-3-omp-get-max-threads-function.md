---
title: "3.1.3 omp_get_max_threads – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e021f0873aa94f53a1218a3278a744a0c7740e65
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads – funkce
**Omp_get_max_threads –** funkce vrátí celé číslo, které se musí být alespoň tak velké, jako je počet vláken, která se použije k vytvoření týmu, pokud paralelní oblast bez **num_threads** – klauzule měla být v tomto bodě došlo v kódu. Formát vypadá takto:  
  
```  
#include <omp.h>  
int omp_get_max_threads(void);  
```  
  
 Následující vyjadřuje dolní mez na hodnotu **omp_get_max_threads –**:  
  
```  
  
threads-used-for-next-team  
 <= omp_get_max_threads  
  
```  
  
 Všimněte si, že pokud používá následné paralelní oblast **num_threads** klauzule požádat o určitý počet vláken, záruku na dolní hranice výsledku **omp_get_max_threads –** žádné dlouho blokování.  
  
 **Omp_get_max_threads –** návratová hodnota funkce lze dynamicky přidělit dostatek místa pro všechna vlákna v týmu vytvořen v následných paralelní oblast.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **omp_get_num_threads –** funkce najdete v tématu [bodu 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37.  
  
-   **omp_set_num_threads –** funkce najdete v tématu [bod 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stránce 36.  
  
-   **omp_set_dynamic –** funkce najdete v tématu [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.  
  
-   **num_threads** klauzule, najdete v části [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.