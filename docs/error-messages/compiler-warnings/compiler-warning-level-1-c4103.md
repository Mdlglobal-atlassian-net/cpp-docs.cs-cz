---
title: Kompilátoru (úroveň 1) upozornění C4103 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4103
dev_langs:
- C++
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f072db4a260d2c83d1dd4b373630cd6e585efc2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4103"></a>C4103 kompilátoru upozornění (úroveň 1)
'název souboru': zarovnání změněno poté, co včetně záhlaví, může být způsobeno chybějícím #pragma pack(pop)  
  
 Okolních ovlivňuje rozložení třídy a běžně, pokud balení změny mezi soubory hlaviček, může dojít k problémům.  
  
 Použít #pragma [pack](../../preprocessor/pack.md)(pop) před ukončením soubor hlaviček, chcete-li vyřešit toto upozornění.  
  
 Následující ukázka generuje C4103:  
  
```  
// C4103.h  
#pragma pack(push, 4)  
  
// defintions and declarations  
  
// uncomment the following line to resolve  
// #pragma pack(pop)  
```  
  
 A pak  
  
```  
// C4103.cpp  
// compile with: /LD /W1  
#include "c4103.h"   // C4103  
```