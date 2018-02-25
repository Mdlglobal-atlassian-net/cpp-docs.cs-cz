---
title: omp_get_dynamic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865104055fc98946c09152f328f4812af0120e64
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ompgetdynamic"></a>omp_get_dynamic
Vrátí hodnotu, která určuje, pokud počet vláken, která je k dispozici v dalších paralelní oblasti lze upravit podle času spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int omp_get_dynamic();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je povoleno nenulové hodnoty, dynamické úpravy vláken.  
  
## <a name="remarks"></a>Poznámky  
 Dynamické přizpůsobení vláken je definován s [omp_set_dynamic –](../../../parallel/openmp/reference/omp-set-dynamic.md) a [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md).  
  
 Další informace najdete v tématu [3.1.7 omp_set_dynamic – funkce](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).  
  
## <a name="example"></a>Příklad  
 V tématu [omp_set_dynamic –](../../../parallel/openmp/reference/omp-set-dynamic.md) příklad použití `omp_get_dynamic`.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)