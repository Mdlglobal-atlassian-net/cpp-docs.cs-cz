---
title: Kompilátoru (úroveň 1) upozornění C4556 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- xml
- C4556
dev_langs:
- C++
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22d10f7dc73e0d5e39fcad8975114f7cb176b24d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4556"></a>C4556 kompilátoru upozornění (úroveň 1)
hodnota argumentu vnitřní okamžitou 'Hodnota' je mimo rozsah 'dolní hranice - horní hranice.  
  
 Vnitřní odpovídá instrukce hardwaru. Instrukce hardwaru má pevný počet bitů ke kódování konstanta. Pokud ***hodnota*** je mimo rozsah, se nebude kódování správně. Kompilátor zkrátí navíc bits.  
  
 Následující ukázka generuje C4556:  
  
```  
// C4556.cpp  
// compile with: /W1  
// processor: x86 IPF  
#include <xmmintrin.h>  
void test()  
{  
   __m64 m;  
   _m_pextrw(m, 5);   // C4556  
}  
int main()  
{  
}  
```