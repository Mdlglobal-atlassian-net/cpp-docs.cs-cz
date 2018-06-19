---
title: Kompilátoru (úroveň 1 a 4) upozornění C4949 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4949
dev_langs:
- C++
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dbf80f85db7334d4bcb46402851cac601d258f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279643"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>C4949 kompilátoru upozornění (úroveň 1 a 4)
direktivy 'spravované' a 'nespravované, dávat smysl jenom v případě, že kompilovat s ' / clr [: možnost].  
  
 Kompilátor ignoruje [spravované](../../preprocessor/managed-unmanaged.md) a nespravované direktivy, pokud není zdrojový kód kompilovat s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). Toto upozornění je informační.  
  
 Následující ukázka generuje C4949:  
  
```  
// C4949.cpp  
// compile with: /LD /W1  
#pragma managed   // C4949  
```  
  
 Když **#pragma nespravované** se používá bez **/CLR**, C4949 je úroveň 4 upozornění.  
  
 Následující ukázka generuje C4949:  
  
```  
// C4949b.cpp  
// compile with: /LD /W4  
#pragma unmanaged   // C4949  
```