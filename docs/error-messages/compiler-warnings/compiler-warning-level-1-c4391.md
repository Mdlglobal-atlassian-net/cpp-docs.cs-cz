---
title: "Kompilátoru (úroveň 1) upozornění C4391 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4391
dev_langs: C++
helpviewer_keywords: C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 91ee6716ee5139da02319925609777ebfec08a56
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4391"></a>C4391 kompilátoru upozornění (úroveň 1)
'podpis': nesprávné návratový typ pro vnitřní funkce očekává "typ"  
  
 Deklarace funkce pro kompilátor vnitřní měl chybný návratový typ. Výsledný obraz nemusí pracovat správně.  
  
 Pokud chcete odstranit toto upozornění, opravte deklaraci nebo odstraňte deklaraci a jednoduše #include na příslušný soubor hlaviček.  
  
 Následující ukázka generuje C4391:  
  
```  
// C4391.cpp  
// compile with: /W1  
// processor: x86  
// uncomment the following line and delete the line that  
// generated the warning to resolve  
// #include "xmmintrin.h"  
  
#ifdef  __cplusplus  
extern "C" {  
#endif  
  
extern void _mm_load_ss(float *p);   // C4391  
  
#ifdef  __cplusplus  
}  
#endif  
  
int main()  
{  
}  
```