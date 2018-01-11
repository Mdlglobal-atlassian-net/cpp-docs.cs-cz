---
title: omp_destroy_lock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_destroy_lock
dev_langs: C++
helpviewer_keywords: omp_destroy_lock OpenMP function
ms.assetid: b73ab036-b76f-4e42-82ff-c89db2edf7c0
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e2dc67a09daaecb4ac30bad404eba7de493501f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ompdestroylock"></a>omp_destroy_lock
Uninitializes zámek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_destroy_lock(  
   omp_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `lock`  
 Proměnné typu [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) který byl inicializován s [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md).  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [3.2.2 omp_destroy_lock a omp_destroy_nest_lock – funkce](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).  
  
## <a name="example"></a>Příklad  
 V tématu [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) příklad použití `omp_destroy_lock`.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)