---
title: Kompilátoru (úroveň 4) upozornění C4408 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4408
dev_langs:
- C++
helpviewer_keywords:
- C4408
ms.assetid: 8488a186-ed1d-425c-aaeb-c72472c1da68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 640a3de24921186bd441b8f8b9bc5f3dcd7e5810
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4408"></a>C4408 kompilátoru upozornění (úroveň 4)
anonymousstruct nebo sjednocení nedeklaruje žádné datové členy  
  
 Sjednocení nebo anonymní struktury musí mít alespoň jeden datový člen.  
  
 Následující ukázka generuje C4408:  
  
```  
// C4408.cpp  
// compile with: /W4 /LD  
static union  
{  
   // int i;  
};  
// a named union can have no data members  
// } MyUnion;  
```