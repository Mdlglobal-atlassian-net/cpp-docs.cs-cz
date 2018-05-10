---
title: 3.1.4 omp_get_thread_num – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad749b91470f7834169fe8ed734f1d627aa228e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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
  
-   `omp_get_num_threads` Funkce, najdete v části [bodu 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37.