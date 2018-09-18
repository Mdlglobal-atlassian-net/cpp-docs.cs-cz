---
title: omp_set_num_threads – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 849bdade5c6abfad07ebed262fb367487d3e1415
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047886"
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads
Nastaví počet vláken v následných paralelních oblastí, pokud nejsou přepsány [num_threads](../../../parallel/openmp/reference/num-threads.md) klauzuli.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
### <a name="parameters"></a>Parametry
  
*num_threads*<br/>
Počet vláken v paralelní oblasti.  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [3.1.1 omp_set_num_threads – funkce](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).  
  
## <a name="example"></a>Příklad  
 Zobrazit [omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md) pro příklad použití `omp_set_num_threads`.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)