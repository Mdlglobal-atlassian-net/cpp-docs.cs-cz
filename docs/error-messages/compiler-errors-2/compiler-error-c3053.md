---
title: "C3053 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3053
dev_langs: C++
helpviewer_keywords: C3053
ms.assetid: ab9a25f3-e341-4f6e-8e69-069b4a963a64
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dc2c7aeedc68b215c030266311db8dc8bac436ce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3053"></a>C3053 chyby kompilátoru
'symbol': "threadprivate" je platná pouze pro globální nebo statické datových položek  
  
 Symboly předaný [threadprivate](../../parallel/openmp/reference/threadprivate.md) musí být buď globální nebo statické.  
  
 Následující ukázka generuje C3053:  
  
```  
// C3053.cpp  
// compile with: /openmp  
void Test() {  
   int x, y;  
   #pragma omp threadprivate(x, y)   // C3053  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```  
  
 Možná řešení:  
  
```  
// C3053b.cpp  
// compile with: /openmp /LD  
int x, y;  
#pragma omp threadprivate(x, y)  
  
void Test() {  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```