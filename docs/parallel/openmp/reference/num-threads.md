---
title: num_threads | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- num_threads
dev_langs:
- C++
helpviewer_keywords:
- num_threads OpenMP clause
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3485d534cf279863b241abcd26195cdde7fea19
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016283"
---
# <a name="numthreads"></a>num_threads
Nastaví počet vláken v týmu vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
num_threads(num)  
```  
  
### <a name="parameters"></a>Parametry
  
*počet*<br/>
Počet vláken  
  
## <a name="remarks"></a>Poznámky  
 `num_threads` Klauzule má stejné funkce jako [omp_set_num_threads –](../../../parallel/openmp/reference/omp-set-num-threads.md) funkce.  
  
 `num_threads` platí pro následující direktivy:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Oddíly](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Další informace najdete v tématu [2.3 parallel – konstrukce](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Příklad  
 Zobrazit [paralelní](../../../parallel/openmp/reference/parallel.md) pro příklad použití `num_threads` klauzuli.  
  
## <a name="see-also"></a>Viz také  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)