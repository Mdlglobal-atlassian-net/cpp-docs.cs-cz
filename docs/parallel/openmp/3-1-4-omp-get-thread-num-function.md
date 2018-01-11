---
title: "3.1.4 omp_get_thread_num – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b7b968d103631dafcdd2132cb749ae8feed30085
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num – funkce
`omp_get_thread_num` Funkce vrátí vlákno počet, v rámci jeho team vláken provádění funkce. Číslo leží vlákno mezi 0 a **omp_get_num_threads()**-1 (včetně). Hlavní vlákno týmu se vlákna 0.  
  
 Formát vypadá takto:  
  
```  
#include <omp.h>  
int omp_get_thread_num(void);  
```  
  
 Pokud je volána z sériové oblasti, `omp_get_thread_num` vrátí hodnotu 0. Pokud je volána v rámci vnořené paralelní oblasti, která je serializováno, funkce vrátí hodnotu 0.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   `omp_get_num_threads`Funkce, najdete v části [bodu 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37.