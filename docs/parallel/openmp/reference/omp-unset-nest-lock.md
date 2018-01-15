---
title: "omp_unset_nest_lock – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_unset_nest_lock
dev_langs: C++
helpviewer_keywords: omp_unset_nest_lock OpenMP function
ms.assetid: 1721d061-3f9c-45d7-b479-a665cd0a121d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cde62972a3f7cd2094f9a23d824e3f244a9968a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ompunsetnestlock"></a>omp_unset_nest_lock
Uvolní nestable zámek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_unset_nest_lock(   
   omp_nest_lock_t *lock   
);  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `lock`  
 Proměnné typu [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) který byl inicializován s [omp_init_nest_lock –](../../../parallel/openmp/reference/omp-init-nest-lock.md), vlákno ve vlastnictví a provádění ve funkci.  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [3.2.4 omp_unset_lock a omp_unset_nest_lock – funkce](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).  
  
## <a name="example"></a>Příklad  
 V tématu [omp_init_nest_lock –](../../../parallel/openmp/reference/omp-init-nest-lock.md) příklad použití `omp_unset_nest_lock`.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)