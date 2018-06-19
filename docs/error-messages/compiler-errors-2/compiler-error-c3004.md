---
title: C3004 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3004
dev_langs:
- C++
helpviewer_keywords:
- C3004
ms.assetid: 819c2b57-8366-4ca7-9135-1f0c5e5b6bb6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c03f9b609bfa7f60794a120488315680e5f6df2d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243584"
---
# <a name="compiler-error-c3004"></a>C3004 chyby kompilátoru
'klauzule': klauzule není platný na "směrnice" OpenMP – direktiva  
  
 Klauzule OpenMP byl použit na direktivu, pro který není povolené.  
  
 Následující ukázka generuje C3004:  
  
```  
// C3004.c  
// compile with: /openmp  
int main()  
{  
   int x, y, z;  
  
   // Shared clause not allowed for 'single' directive.  
   #pragma omp single shared(x, y)   // C3004  
  
   x = y;  
}  
```