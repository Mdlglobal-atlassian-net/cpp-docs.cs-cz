---
title: num_threads | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: num_threads
dev_langs: C++
helpviewer_keywords: num_threads OpenMP clause
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7289a843c33fbc9ba23d6006997dea8e09ba7c79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="numthreads"></a>num_threads
Nastaví počet vláken v týmu přístup z více vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
num_threads(num)  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `num`  
 Počet vláken  
  
## <a name="remarks"></a>Poznámky  
 `num_threads` Klauzule má stejné funkce jako [omp_set_num_threads –](../../../parallel/openmp/reference/omp-set-num-threads.md) funkce.  
  
 `num_threads`platí pro následující direktivy:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [oddíly](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Další informace najdete v tématu [2.3 parallel – konstrukce](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Příklad  
 V tématu [paralelní](../../../parallel/openmp/reference/parallel.md) příklad použití `num_threads` klauzule.  
  
## <a name="see-also"></a>Viz také  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)