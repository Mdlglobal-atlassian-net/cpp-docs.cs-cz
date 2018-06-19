---
title: Kompilátoru (úroveň 4) upozornění C4668 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4668
dev_langs:
- C++
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08a6349e867382a327f53676583f5daad7df80dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294333"
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