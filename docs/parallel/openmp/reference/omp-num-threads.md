---
title: OMP_NUM_THREADS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- OMP_NUM_THREADS
dev_langs:
- C++
helpviewer_keywords:
- OMP_NUM_THREADS OpenMP environment variable
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 077a709d70e19e62133e5b48e42f2e53ac7c835f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ompnumthreads"></a>OMP_NUM_THREADS
Nastaví maximální počet vláken v oblasti paralelní, není-li přepsat [omp_set_num_threads –](../../../parallel/openmp/reference/omp-set-num-threads.md) nebo [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `num`  
 Maximální počet vláken, která chcete v oblasti paralelní až 64 implementace Visual C++.  
  
## <a name="remarks"></a>Poznámky  
 **OMP_NUM_THREADS** – proměnná prostředí je možné přepsat [omp_set_num_threads –](../../../parallel/openmp/reference/omp-set-num-threads.md) funkce nebo [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
 Výchozí hodnota `num` v jazyce Visual C++ implementace standardní OpenMP je počet virtuálních procesorů, včetně procesorů Hyper-threadingem.  
  
 Další informace najdete v tématu [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz nastaví **OMP_NUM_THREADS** proměnnou prostředí na 16:  
  
```  
set OMP_NUM_THREADS=16  
```  
  
 Následující příkaz zobrazí aktuální nastavení **OMP_NUM_THREADS** proměnnou prostředí:  
  
```  
set OMP_NUM_THREADS  
```  
  
## <a name="see-also"></a>Viz také  
 [Proměnné prostředí](../../../parallel/openmp/reference/openmp-environment-variables.md)