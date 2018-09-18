---
title: Upozornění (úroveň 3) C4738 kompilátoru | Dokumentace Microsoftu
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
ms.openlocfilehash: 8e017ef94dd28de8d4c66ab89b1509f755beeb07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053217"
---
# <a name="compiler-warning-level-3-c4738"></a>Kompilátor upozornění (úroveň 3) C4738

ukládání 32bitového plovoucího výsledku do paměti, možná ztráta

C4738 varuje, že argument předaný výsledek přiřazení, přetypování, nebo jiné operace možná bude nutné se zaokrouhlí nebo že operace nemá dostatek registrů a nutné k využití paměti (přesunutí). To může vést ke ztrátě výkonu.

Pokud chcete vyřešit toto upozornění a vyhněte se zaokrouhluje se směrem, proveďte kompilaci s [Fast](../../build/reference/fp-specify-floating-point-behavior.md) nebo použijte `double` místo `float`.

Pokud chcete vyřešit toto upozornění a vyhněte se došly registrů, změnit pořadí výpočet a upravovat vaše užívání vkládání

Toto upozornění je vypnuto ve výchozím nastavení. Další informace najdete v tématu [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

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