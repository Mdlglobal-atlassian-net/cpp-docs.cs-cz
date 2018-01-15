---
title: "omp_set_nest_lock – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_set_nest_lock
dev_langs: C++
helpviewer_keywords: omp_set_nest_lock OpenMP function
ms.assetid: b98ed889-ff8e-4217-a3e9-3993ed8699af
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d073a932eff9a73d861902c3bb8a2ef00870e74b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ompsetnestlock"></a>omp_set_nest_lock
Bloky vláken provádění, dokud nebude k dispozici zámek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_set_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `lock`  
 Proměnné typu [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) který byl inicializován s [omp_init_nest_lock –](../../../parallel/openmp/reference/omp-init-nest-lock.md).  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [3.2.3 omp_set_lock a omp_set_nest_lock – funkce](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).  
  
## <a name="examples"></a>Příklady  
 V tématu [omp_init_nest_lock –](../../../parallel/openmp/reference/omp-init-nest-lock.md) příklad použití `omp_set_nest_lock`.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)