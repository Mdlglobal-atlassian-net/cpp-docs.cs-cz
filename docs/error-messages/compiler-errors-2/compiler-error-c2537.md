---
title: C2537 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2537
dev_langs:
- C++
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6100f77d3a1487bfa1eb12a78ac8187cec43fe64
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199954"
---
# <a name="compiler-error-c2537"></a>C2537 chyby kompilátoru
'specifikátor': specifikace neplatný propojení  
  
 Možné příčiny:  
  
1.  Specifikátor propojení není podporována. Je podporován pouze specifikátor propojení "C".  
  
2.  "C" propojení je určené pro více než jednu funkci v sadě přetížených funkcí. Toto není povoleno.  
  
 Následující ukázka generuje C2537:  
  
```  
// C2537.cpp  
// compile with: /c  
extern "c" void func();   // C2537  
extern "C" void func2();   // OK  
```