---
title: Upozornění kompilátoru (úroveň 3) C4738
ms.date: 11/04/2016
f1_keywords:
- C4738
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
ms.openlocfilehash: c1989518c3965f8faa54a05b2925d0e37455625e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991703"
---
# <a name="compiler-warning-level-3-c4738"></a>Upozornění kompilátoru (úroveň 3) C4738

ukládání 32bitového plovoucího výsledku do paměti, možná ztráta

C4738 upozorňuje na to, že výsledek přiřazení, přetypování, předaného argumentu nebo jiné operace může být potřeba zaokrouhlit nebo že operace skončila s registry a je potřeba k využití paměti (v rozlití). To může mít za následek ztrátu výkonu.

Chcete-li vyřešit toto upozornění a vyhnout se zaokrouhlování, zkompilujte pomocí [/FP: Fast](../../build/reference/fp-specify-floating-point-behavior.md) nebo použijte `double` místo `float`.

Chcete-li vyřešit toto upozornění a vyhnout se nedostatku registru, změňte pořadí výpočtu a upravte své používání pro vkládání

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4738:

```cpp
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
