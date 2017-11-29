---
title: "Kompilátoru (úroveň 4) upozornění C4668 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4668
dev_langs: C++
helpviewer_keywords: C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 059bf2dcb2d854ad05d21a9314d0d6a3f2a7a432
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4668"></a>C4668 kompilátoru upozornění (úroveň 4)
'symbol' není definován jako preprocesor makro, nahraďte '0' pro 'directives'  
  
 Symbol, který není definovaný se použila se direktivy preprocesoru. Symbol bude vyhodnocena jako false. Chcete-li definovat symbol, můžete použít buď [#define – direktiva](../../preprocessor/hash-define-directive-c-cpp.md) nebo [/D](../../build/reference/d-preprocessor-definitions.md) – možnost kompilátoru.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4668:  
  
```  
// C4668.cpp  
// compile with: /W4  
#include <stdio.h>  
  
#pragma warning (default : 4668)   // turn warning on  
  
int main()   
{  
    #if q   // C4668, q is not defined  
        printf_s("defined");  
    #else  
        printf_s("undefined");  
    #endif  
}  
```