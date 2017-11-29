---
title: "C3055 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3055
dev_langs: C++
helpviewer_keywords: C3055
ms.assetid: 60446ee0-18dd-48fc-9059-f0a14229dce8
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b85138c6183598c8db2ab89099aa66940f60e8cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3055"></a>C3055 chyby kompilátoru
'symbol': symbol nelze odkazovat, než bude použit v direktivě 'threadprivate.  
  
 Symbol se odkazuje a pak se použije v [threadprivate](../../parallel/openmp/reference/threadprivate.md) klauzule, což není povoleno.  
  
 Následující ukázka generuje C3055:  
  
```  
// C3055.cpp  
// compile with: /openmp  
int x, y;  
int z = x;  
#pragma omp threadprivate(x, y)   // C3055  
  
void test() {  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```  
  
 Možná řešení:  
  
```  
// C3055b.cpp  
// compile with: /openmp /LD  
int x, y, z;  
#pragma omp threadprivate(x, y)  
  
void test() {  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```