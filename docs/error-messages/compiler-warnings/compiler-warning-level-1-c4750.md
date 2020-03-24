---
title: Upozornění kompilátoru (úroveň 1) C4750
ms.date: 11/04/2016
f1_keywords:
- C4750
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
ms.openlocfilehash: 9ba0a37d2c213c35002b8e09d4377869a868d401
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175165"
---
# <a name="compiler-warning-level-1-c4750"></a>Upozornění kompilátoru (úroveň 1) C4750

' identifier ': funkce s _alloca () je vložena do smyčky

Funkce Identifier vynutí vložené rozšíření [_alloca](../../c-runtime-library/reference/alloca.md) funkce v rámci smyčky, což může způsobit přetečení zásobníku při spuštění smyčky.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Ujistěte se, že funkce identifikátor není upravena pomocí specifikátoru [__forceinline](../../cpp/inline-functions-cpp.md) .

1. Zajistěte, aby funkce identifikátor neobsahuje funkci [_alloca](../../c-runtime-library/reference/alloca.md) , která je obsažená ve smyčce.

1. Nezadávejte přepínač kompilace [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/Ox](../../build/reference/ox-full-optimization.md)nebo [/og](../../build/reference/og-global-optimizations.md) .

1. Umístěte funkci [_alloca](../../c-runtime-library/reference/alloca.md) do [příkazu try-except](../../cpp/try-except-statement.md) , který bude zachytit přetečení zásobníku.

## <a name="example"></a>Příklad

Následující příklad kódu volá `MyFunction` ve smyčce a `MyFunction` volá funkci `_alloca`. Modifikátor `__forceinline` způsobí vložené rozšíření `_alloca` funkce.

```cpp
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
