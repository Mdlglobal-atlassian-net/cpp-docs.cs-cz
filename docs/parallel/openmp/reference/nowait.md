---
title: nowait | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: nowait
dev_langs: C++
helpviewer_keywords: nowait OpenMP clause
ms.assetid: 8a74265d-879c-46cf-8071-a1084f24f16e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c5cc3f82334752854300c683b9aa1b02c7e94791
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nowait"></a>nowait
Přepíše implicitní v direktivě bariéry.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
nowait  
```  
  
## <a name="remarks"></a>Poznámky  
 `nowait`platí pro následující direktivy:  
  
-   [pro](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [oddíly](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [jeden](../../../parallel/openmp/reference/single.md)  
  
 Další informace najdete v tématu [2.4.1 for – konstrukce](../../../parallel/openmp/2-4-1-for-construct.md), [2.4.2 sections – konstrukce](../../../parallel/openmp/2-4-2-sections-construct.md), a [2.4.3 jeden vytvořit](../../../parallel/openmp/2-4-3-single-construct.md).  
  
## <a name="example"></a>Příklad  
  
```  
// omp_nowait.cpp  
// compile with: /openmp /c  
#include <stdio.h>  
  
#define SIZE 5  
  
void test(int *a, int *b, int *c, int size)   
{  
    int i;  
    #pragma omp parallel  
    {  
        #pragma omp for nowait  
        for (i = 0; i < size; i++)  
            b[i] = a[i] * a[i];  
  
        #pragma omp for nowait  
        for (i = 0; i < size; i++)  
            c[i] = a[i]/2;  
    }  
}  
  
int main( )   
{  
    int a[SIZE], b[SIZE], c[SIZE];  
    int i;  
  
    for (i=0; i<SIZE; i++)  
        a[i] = i;  
  
    test(a,b,c, SIZE);  
  
    for (i=0; i<SIZE; i++)  
        printf_s("%d, %d, %d\n", a[i], b[i], c[i]);  
}  
```  
  
```Output  
0, 0, 0  
1, 1, 0  
2, 4, 1  
3, 9, 1  
4, 16, 2  
```  
  
## <a name="see-also"></a>Viz také  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)