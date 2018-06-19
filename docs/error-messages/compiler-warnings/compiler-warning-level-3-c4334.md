---
title: Kompilátoru (úroveň 3) upozornění C4334 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4334
dev_langs:
- C++
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f26749c968c3cac18b509046633ba3d91d15a4be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292682"
---
# <a name="compiler-warning-level-3-c4334"></a>C4334 kompilátoru upozornění (úroveň 3)
'operátor': výsledek 32-bit shift implicitně převést na 64 bitů (byla určena shift 64-bit?)  
  
 Výsledek 32-bit shift byl implicitně převést na 64bitovou a kompilátoru má podezření, že byla určena shift 64-bit.  Toto upozornění vyřešíte buď použijte shift 64-bit nebo explicitně přetypovat výsledek shift na 64bitovou verzi.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4334.  
  
```  
// C4334.cpp  
// compile with: /W3 /c  
void SetBit(unsigned __int64 *p, int i) {  
   *p |= (1 << i);   // C4334  
   *p |= (1i64 << i);   // OK  
}  
```