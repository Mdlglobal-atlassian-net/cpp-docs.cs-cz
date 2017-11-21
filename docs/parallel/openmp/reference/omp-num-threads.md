---
title: OMP_NUM_THREADS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_NUM_THREADS
dev_langs: C++
helpviewer_keywords: OMP_NUM_THREADS OpenMP environment variable
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2139ecfc719bd6e5836a67d9387b3ff2f4289bc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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