---
title: "Kompilátoru (úroveň 1) upozornění C4392 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4392
dev_langs: C++
helpviewer_keywords: C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c33a88ae9dda253192fc6ed4616da52ef7c58c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4392"></a>C4392 kompilátoru upozornění (úroveň 1)
'podpis': nesprávný počet argumentů pro vnitřní funkce očekává, číslo' argumenty  
  
 Deklarace funkce pro kompilátor vnitřní měla nesprávný počet argumentů. Výsledný obraz nemusí pracovat správně.  
  
 Pokud chcete odstranit toto upozornění, opravte deklaraci nebo odstraňte deklaraci a jednoduše #include na příslušný soubor hlaviček.  
  
 Následující ukázka generuje C4392:  
  
```  
// C4392.cpp  
// compile with: /W1  
// processor: x86  
// uncomment the following line and delete the line that  
// generated the warning to resolve  
// #include "xmmintrin.h"  
  
#ifdef  __cplusplus  
extern "C" {  
#endif  
  
extern void _mm_stream_pd(double *dp);   // C4392  
  
#ifdef  __cplusplus  
}  
#endif  
  
int main()  
{  
}  
```