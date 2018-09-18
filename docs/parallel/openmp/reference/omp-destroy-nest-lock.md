---
title: omp_destroy_nest_lock – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_destroy_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_destroy_nest_lock OpenMP function
ms.assetid: 0ab1352b-668f-43dd-b441-31ec4cc53e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37ac75158705a26b10b077652f51396dcd591740
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104039"
---
# <a name="ompdestroynestlock"></a>omp_destroy_nest_lock
Zruší inicializaci, vnořitelných zámek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_destroy_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
### <a name="parameters"></a>Parametry
  
*lock*<br/>
Proměnné typu [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) , který byl inicializován s [omp_init_nest_lock –](../../../parallel/openmp/reference/omp-init-nest-lock.md).  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [3.2.2 omp_destroy_lock a omp_destroy_nest_lock – funkce](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).  
  
## <a name="example"></a>Příklad  
 Zobrazit [omp_init_nest_lock –](../../../parallel/openmp/reference/omp-init-nest-lock.md) pro příklad použití `omp_destroy_nest_lock`.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)