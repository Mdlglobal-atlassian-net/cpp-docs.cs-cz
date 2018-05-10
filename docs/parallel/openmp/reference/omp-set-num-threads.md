---
title: omp_set_num_threads – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 335cb283026a019d6c6a03565c5dbec541140db3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads
Nastaví počet vláken v následujících oblastech paralelní, není-li přepsat [num_threads](../../../parallel/openmp/reference/num-threads.md) klauzule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `num_threads`  
 Počet vláken v paralelní oblasti.  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [3.1.1 omp_set_num_threads – funkce](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).  
  
## <a name="example"></a>Příklad  
 V tématu [omp_get_num_threads –](../../../parallel/openmp/reference/omp-get-num-threads.md) příklad použití `omp_set_num_threads`.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)