---
title: Kompilátoru (úroveň 3) upozornění C4738 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4738
dev_langs:
- C++
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50b94cde2f8809b8ce56dc599804d11b8d058166
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4738"></a>C4738 kompilátoru upozornění (úroveň 3)
ukládání 32bitového plovoucího výsledku do paměti, možná ztráta  
  
 C4738 varuje výsledek přiřazení, cast. předaný argument, nebo má být zaokrouhleno může potřebovat jiná operace, nebo že operaci nedostatku registry a potřeba k použití paměti (přesahu). To může dojít ke ztrátě výkonu.  
  
 Toto upozornění vyřešit a zamezit tak zaokrouhlení, kompilovat s [/fp:fast](../../build/reference/fp-specify-floating-point-behavior.md) nebo použijte `double` místo `float`.  
  
 Vyřešte toto upozornění a zamezit tak nedošly registrů, změňte pořadí výpočtu a upravit používání vložené  
  
 Toto upozornění je ve výchozím nastavení vypnutý. Další informace najdete v tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4738:  
  
```  
// C4738.cpp  
// compile with: /c /fp:precise /O2 /W3  
// processor: x86  
#include <stdio.h>  
  
#pragma warning(default : 4738)  
  
float func(float f)  
{  
    return f;  
}  
  
int main()  
{  
    extern float f, f1, f2;  
    double d = 0.0;  
  
    f1 = func(d);  
    f2 = (float) d;  
    f = f1 + f2;   // C4738  
    printf_s("%f\n", f);  
}  
```