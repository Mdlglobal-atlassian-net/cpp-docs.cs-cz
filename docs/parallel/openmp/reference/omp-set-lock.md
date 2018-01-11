---
title: omp_set_lock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_set_lock
dev_langs: C++
helpviewer_keywords: omp_set_lock OpenMP function
ms.assetid: ded839cb-ca19-403f-8622-eb52ce512d31
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 97ea221d07de8accad22d9bab1fee2b73c6345a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ompsetlock"></a>omp_set_lock
Bloky vláken provádění, dokud nebude k dispozici zámek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_set_lock(  
   omp_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `lock`  
 Proměnné typu [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) který byl inicializován s [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md).  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [3.2.3 omp_set_lock a omp_set_nest_lock – funkce](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).  
  
## <a name="examples"></a>Příklady  
 V tématu [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) příklad použití `omp_set_lock`.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)