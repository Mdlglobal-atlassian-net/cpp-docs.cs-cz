---
title: "Kompilátoru (úroveň 1) upozornění C4470 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4470
dev_langs: C++
helpviewer_keywords: C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e77fa078dd3263f796c7b136068e10567da3e0d8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4470"></a>C4470 kompilátoru upozornění (úroveň 1)
direktivy s plovoucí desetinnou čárkou řízení ignorovat v/CLR  
  
 Float – ovládací prvek direktivy:  
  
-   [fenv_access –](../../preprocessor/fenv-access.md)  
  
-   [float_control –](../../preprocessor/float-control.md)  
  
-   [fp_contract –](../../preprocessor/fp-contract.md)  
  
 nemají vliv pod [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Následující ukázka generuje C4470:  
  
```  
// C4470.cpp  
// compile with: /clr /W1 /LD  
#pragma float_control(except, on)   // C4470  
```