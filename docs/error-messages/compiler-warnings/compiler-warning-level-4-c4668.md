---
title: Upozornění kompilátoru (úroveň 4) C4668
ms.date: 11/04/2016
f1_keywords:
- C4668
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
ms.openlocfilehash: 84834ce0f980502e16a8398d35da85d1a005c9cb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990559"
---
# <a name="compiler-warning-level-4-c4668"></a>Upozornění kompilátoru (úroveň 4) C4668

'symbol' není definován jako preprocesor makro, nahraďte '0' pro 'directives'

Symbol, který nebyl definován, byl použit s direktivou preprocesoru. Symbol se vyhodnotí jako NEPRAVDA. Chcete-li definovat symbol, můžete použít buď [direktivu #define](../../preprocessor/hash-define-directive-c-cpp.md) , nebo [/d](../../build/reference/d-preprocessor-definitions.md) možnost kompilátoru.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4668:

```cpp
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
