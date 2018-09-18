---
title: omp_destroy_lock | Dokumentace Microsoftu
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
ms.openlocfilehash: 5c24f09bbad550633c68c403c89362a293265111
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019921"
---
# <a name="ompdestroylock"></a>omp_destroy_lock
Zruší inicializaci zámek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_destroy_lock(  
   omp_lock_t *lock  
);  
```  
  
### <a name="parameters"></a>Parametry
  
*lock*<br/>
Proměnné typu [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) , který byl inicializován s [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md).  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [3.2.2 omp_destroy_lock a omp_destroy_nest_lock – funkce](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).  
  
## <a name="example"></a>Příklad  
 Zobrazit [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) pro příklad použití `omp_destroy_lock`.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)