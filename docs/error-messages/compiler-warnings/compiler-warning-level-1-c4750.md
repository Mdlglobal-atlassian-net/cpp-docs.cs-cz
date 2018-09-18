---
title: Upozornění (úroveň 1) C4750 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4750
dev_langs:
- C++
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c77c46daf30b6e0238345d9b2be3c6c5362c192
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026618"
---
# <a name="compiler-warning-level-1-c4750"></a>Kompilátor upozornění (úroveň 1) C4750

'identifier': funkce s: _alloca() je vložená do smyčky

'Identifier' funkce vynutí vložené rozšíření [_alloca](../../c-runtime-library/reference/alloca.md) funkce v rámci smyčky, což by mohlo způsobit přetečení zásobníku při provedení smyčky.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Ujistěte se, že funkce 'identifier' není upraven pomocí [__forceinline](../../cpp/inline-functions-cpp.md) specifikátor.

1. Ujistěte se, že funkce 'identifier' neobsahuje [_alloca](../../c-runtime-library/reference/alloca.md) funkce, které jsou obsaženy ve smyčce.

1. Nezadávejte [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/Ox](../../build/reference/ox-full-optimization.md), nebo [/og](../../build/reference/og-global-optimizations.md) kompilaci přepínače.

1. Místo [_alloca](../../c-runtime-library/reference/alloca.md) fungovat v [zkuste-except – příkaz](../../cpp/try-except-statement.md) , který zachytí přetečení zásobníku.

## <a name="example"></a>Příklad

Následující příklad volá kódu `MyFunction` ve smyčce, a `MyFunction` volání `_alloca` funkce. `__forceinline` Modifikátor způsobí, že vložené rozšíření `_alloca` funkce.

```
// c4750.cpp
// compile with: /O2 /W1 /c
#include <intrin.h>

char * volatile newstr;

__forceinline void myFunction(void) // C4750 warning
{
// The _alloca function does not require a __try/__except
// block because the example uses compiler option /c.
    newstr = (char * volatile) _alloca(1000);
}

int main(void)
{
    for (int i=0; i<50000; i++)
       myFunction();
    return 0;
}
```

## <a name="see-also"></a>Viz také

[_alloca](../../c-runtime-library/reference/alloca.md)