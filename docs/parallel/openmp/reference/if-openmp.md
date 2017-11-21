---
title: Pokud (OpenMP) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: if
dev_langs: C++
helpviewer_keywords: if OpenMP clause
ms.assetid: db5940b6-2414-4bf8-934d-3edd8393c0f8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 381347686d8e63681b5d179e191546b8a5bf2f8b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="if-openmp"></a>if (OpenMP)
Určuje, zda se má provést smyčku paralelně nebo postupně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
if(expression)  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `expression`  
 Integrální výraz, který, pokud se vyhodnotí jako true (nenulové hodnoty), způsobí, že kód v oblasti paralelní prováděny paralelně. Pokud je výsledkem na hodnotu false (nula), paralelní oblast je provedený postupně (jedno vlákno).  
  
## <a name="remarks"></a>Poznámky  
 `if`platí pro následující direktivy:  
  
-   [paralelní](../../../parallel/openmp/reference/parallel.md)  
  
-   [pro](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [oddíly](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Další informace najdete v tématu [2.3 parallel – konstrukce](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Příklad  
  
```  
// omp_if.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
void test(int val)  
{  
    #pragma omp parallel if (val)  
    if (omp_in_parallel())  
    {  
        #pragma omp single  
        printf_s("val = %d, parallelized with %d threads\n",  
                 val, omp_get_num_threads());  
    }  
    else  
    {  
        printf_s("val = %d, serialized\n", val);  
    }  
}  
  
int main( )  
{  
    omp_set_num_threads(2);  
    test(0);  
    test(2);  
}  
```  
  
```Output  
val = 0, serialized  
val = 2, parallelized with 2 threads  
```  
  
## <a name="see-also"></a>Viz také  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)