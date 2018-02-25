---
title: Atomic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atomic
dev_langs:
- C++
helpviewer_keywords:
- atomic OpenMP directive
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8cd00244d4668821942e7d6a9f6873652002bddb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="atomic"></a>atomic
Určuje, že umístění paměti, který bude aktualizován atomicky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### <a name="parameters"></a>Parametry  
 `expression`  
 Příkaz obsahující lvalue jejichž umístění paměti, které chcete chránit proti více zápisy. Další informace o forms právní výrazu najdete v OpenMP specifikaci.  
  
## <a name="remarks"></a>Poznámky  
 `atomic` – Direktiva podporuje žádné OpenMP – klauzule.  
  
 Další informace najdete v tématu [2.6.4 atomic vytvořit](../../../parallel/openmp/2-6-4-atomic-construct.md).  
  
## <a name="example"></a>Příklad  
  
```  
// omp_atomic.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
#define MAX 10  
  
int main() {  
   int count = 0;  
   #pragma omp parallel num_threads(MAX)  
   {  
      #pragma omp atomic  
      count++;  
   }  
   printf_s("Number of threads: %d\n", count);  
}  
```  
  
```Output  
Number of threads: 10  
```  
  
## <a name="see-also"></a>Viz také  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)