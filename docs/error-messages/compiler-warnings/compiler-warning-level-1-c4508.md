---
title: Kompilátoru (úroveň 1) upozornění C4508 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4508
dev_langs:
- C++
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53f152c2f3573e5f3bd7b8e9be0603ed6d3f11bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283193"
---
# <a name="compiler-warning-level-1-c4508"></a>C4508 kompilátoru upozornění (úroveň 1)
'function': funkce by měla vrátit hodnotu; 'void' návratový typ předpokládá, že  
  
 Funkce nemá návratový typ zadaný. V takovém případě by také fire C4430 a kompilátor implementuje potíže hlášené C4430 (výchozí hodnota je int).  
  
 Toto upozornění vyřešíte explicitně deklarujte návratový typ funkce.  
  
 Následující ukázka generuje C4508:  
  
```  
// C4508.cpp  
// compile with: /W1 /c  
#pragma warning (disable : 4430)  
func() {}   // C4508  
void func2() {}   // OK  
```