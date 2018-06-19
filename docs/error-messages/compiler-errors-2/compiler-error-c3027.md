---
title: C3027 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3027
dev_langs:
- C++
helpviewer_keywords:
- C3027
ms.assetid: 6562a5c2-2f28-4b36-91ca-2a64c0f0501a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1616d5b3d493c7e6fd2c9eff6041a43f064713e6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248629"
---
# <a name="compiler-error-c3027"></a>C3027 chyby kompilátoru
'klauzule': byl očekáván výraz aritmetické nebo ukazatele  
  
 Klauzuli, která vyžaduje aritmetické nebo ukazatel výraz byl předán jiný druh výraz.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3027:  
  
```  
// C3027.cpp  
// compile with: /openmp /link vcomps.lib  
#include <stdio.h>  
#include "omp.h"  
  
struct MyStruct   
{  
    int x;  
} m_MyStruct;  
  
int main()   
{  
    int i;  
  
    puts("Test with class MyStruct:\n");  
    #pragma omp parallel for if(m_MyStruct)   // C3027  
    for (i = 1; i <= 2; ++i)  
        printf_s("Hello World - thread %d - iteration %d\n",  
                 omp_get_thread_num(), i);  
  
    puts("Test with int:\n");  
    #pragma omp parallel for if(9)   // OK  
    for (i = 1; i <= 2; ++i)  
        printf_s("Hello World - thread %d - iteration %d\n",  
                 omp_get_thread_num(), i);  
}  
```