---
title: omp_destroy_lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_destroy_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_destroy_lock OpenMP function
ms.assetid: b73ab036-b76f-4e42-82ff-c89db2edf7c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05612664b50c6a51008ab1d78ac1d40145fb593e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695002"
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