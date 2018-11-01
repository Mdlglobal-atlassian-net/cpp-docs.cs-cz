---
title: Kompilátor upozornění (úroveň 4) C4668
ms.date: 11/04/2016
f1_keywords:
- C4668
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
ms.openlocfilehash: 11d96941a1efddde87068af8829e24259f2fa312
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529971"
---
# <a name="compiler-warning-level-4-c4668"></a>Kompilátor upozornění (úroveň 4) C4668

'symbol' není definován jako preprocesor makro, nahraďte '0' pro 'directives'

Symbol, který nebyl definován použil se direktiva preprocesoru. Symbol vyhodnotí na hodnotu false. Chcete-li definovat symbol, můžete použít buď [#define – direktiva](../../preprocessor/hash-define-directive-c-cpp.md) nebo [/D](../../build/reference/d-preprocessor-definitions.md) – možnost kompilátoru.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

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