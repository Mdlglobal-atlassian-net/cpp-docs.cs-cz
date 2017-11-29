---
title: "Upozornění (úroveň 1) C4730 kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4730
dev_langs: C++
helpviewer_keywords: C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c27a63b826249c094b507eb4efb3041ab8147973
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4730"></a>Upozornění kompilátoru (úroveň 1) C4730
"hlavní": kombinování _m64 a plovoucí bodu výrazy může vést k nesprávným kódem  
  
 Používá funkci [__m64](../../cpp/m64.md) a **float**/**dvojité** typy. Protože MMX a zaregistruje se s plovoucí desetinnou čárkou sdílí stejný fyzický zaregistrovat místa (nelze používat současně s), pomocí `__m64` a **float**/**dvojité** typy ve stejné funkce může způsobit poškození dat, což může způsobit výjimku.  
  
 Bezpečně používat `__m64` typy a typy s plovoucí desetinnou čárkou v stejnou funkci, každý instrukce, který používá jeden z typů musí být odděleny **_m_empty()** (pro MMX) nebo **_m_femms()** (pro 3DNow!) vnitřní funkce.  
  
 Následující ukázka generuje C4730:  
  
```  
// C4730.cpp  
// compile with: /W1  
// processor: x86  
#include "mmintrin.h"  
  
void func(double)  
{  
}  
  
int main(__m64 a, __m64 b)  
{  
   __m64 m;  
   double f;  
   f = 1.0;  
   m = _m_paddb(a, b);  
   // uncomment the next line to resolve C4730  
   // _m_empty();  
   func(f * 3.0);   // C4730  
}  
```