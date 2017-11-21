---
title: "Kompilátoru (úroveň 1 a 4) upozornění C4949 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4949
dev_langs: C++
helpviewer_keywords: C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 241e0295b16ae350cec213bf25b93f7ad72a0808
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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